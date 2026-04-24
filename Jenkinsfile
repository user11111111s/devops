pipeline {
    agent any

    tools {
        maven 'Maven-3.9.12'   // must match Jenkins tool name
        jdk 'jdk-21'           // must match your JDK name
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/user11111111s/devops.git'
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-creds',
                        url: 'http://localhost:8081'
                    )
                ],
                contextPath: 'hello-world',
                war: 'target/*.war'
            }
        }
    }
}
