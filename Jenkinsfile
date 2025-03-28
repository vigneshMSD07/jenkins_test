pipeline {
    agent any
    
    tools {
        maven "MVN3"
    }
    
    stages {
        stage ('pull scm') {
            steps {
                git credentialsId: 'github', url: 'git@github.com:vigneshMSD07/jenkins_test.git'
            }
        }
        
        stage('build') {
            steps {
                sh "mvn -f api-gateway/ clean package"
            }
        }
        
        stage('archival') {
            steps {
                archiveArtifacts artifacts: 'api-gateway/target/*.jar', followSymlinks: false
            }
        }
        stage('publish') {
            steps {
                junit stdioRetention: '', testResults: 'api-gateway/target/surefire-reports/*.xml'
            }
        }
        stage('test') {
            steps {
                sh 'echo testing'
            }
        }
    }
}
