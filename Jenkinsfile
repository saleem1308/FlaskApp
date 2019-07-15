node {
    def app

    stage('Cloning repository'){
        git credentialsId: 'gitrepo', url: 'https://github.com/saleem1308/FlaskApp.git'
    }

    stage('Building image'){
        app = docker.build("saleem1308/secondjobimage")
    }

    stage('Test image') {

        app.inside {
            echo "Tests passed"
	}
    }

    stage('Push image'){
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
            }
            echo "Trying to Push Docker Build to DockerHub"
    }
    
}
