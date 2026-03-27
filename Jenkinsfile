pipeline {
    agent any

    environment {
        IMAGE_NAME = "flask-app"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop flask-app || true
                docker rm flask-app || true
                docker run -d -p 5000:5000 --name flask-app $IMAGE_NAME
                '''
            }
        }
    }
}