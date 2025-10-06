pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 khasimshaik4/repo:movie'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker') {
                        sh 'docker push khasimshaik4/repo:movie'
                    }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 khasimshaik4/repo:movie'
            }
        }
    }
}
