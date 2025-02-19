pipeline {
    agent { label 'slave3' }
    stages {
        stage('Checkout') {
            steps {
                sh "rm -rf clinic"
                sh "git clone https://github.com/poojagowda-j/clinic.git"
                sh "cd clinic"
            }
        }
stage('installingjava') {
            steps {
            echo " installing java 17"
            sh "sudo apt update"
            sh "sudo apt install -y openjdk-17-jdk"
            }
        }
        stage('Set up Environment') {
            steps {
                sh 'export JAVA_HOME=$(dirname $(dirname $(readlink -f $(which java))))'
                sh 'export MAVEN_HOME=/usr/share/maven'
            }
        }
        stage('build') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('Run Application') {
            steps {
                echo 'Running Spring Boot application...'
                sh 'mvn spring-boot:run'
               
            }
        }
    }
}
