pipeline {
    agent any
    tools {
        maven 'maven'  
    }

    stages {
        stage('Pull the source code') {
            steps {
                git branch: 'main', url: 'https://github.com/prajwal1014/springboot.git '
            }
        }

        stage('Build Application') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Stop Existing Application') {
            steps {
                sh "pkill -f 'spring_app_sak-0.0.1-SNAPSHOT.jar' || true"
                 }
        }
        stage('Deploy Application') {
            steps {
                sh "sudo java -jar target/spring_app_sak-0.0.1-SNAPSHOT.jar > /dev/null 2&1 &"
            }
        }
    

    }
}

