
pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'
    }

    stages {
        stage('clean') {
            steps {
                bat 'mvn clean'
            }
        }

        stage('install') {
            steps {
                bat 'mvn install'
            }
        }

        stage('test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('package') {
            steps {
                bat 'mvn package'
            }
        }
    }

    post {
        success {
            emailext(
                subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build completed successfully.",
                to: "samanvi.chidambaram@gmail.com"
            )
        }

        failure {
            emailext(
                subject: "FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build failed. Check the Jenkins console output.",
                to: "samanvi.chidambaram@gmail.com"
            )
        }
    }
}
