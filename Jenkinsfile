pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/npk62/jenkin-test.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('my-python-app')
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    docker.image('my-python-app').inside {
                        sh 'python -m unittest discover tests/'
                    }
                }
            }
        }
    }
}
