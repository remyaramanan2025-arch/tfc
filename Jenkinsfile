pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f mycontainer || true'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 80:80 --name mycontainer myapp'
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }

        failure {
            echo 'Deployment failed!'
        }
    }
}
