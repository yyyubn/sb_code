pipeline {
    agent any
    
    tools {
        maven 'my_maven'
    }
    environment {
        GITNAME='yyyubn'
        GITMAIL='yyyubn1@gmail.com'
        GITWEBADD='https://github.com/yyyubn/sb_code.git'
        GITSSHADD='git@github.com:yyyubn/sb_code.git'
        GITCREDENTIAL='git_cre'
    }
    
    stages {
        stage('Checkout Github') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [],
                userRemoteConfigs: [[credentialsId: GITCREDENTIAL, url: GITWEBADD]]])
            }
            
            post {
        
                failure {
                    echo 'Repository clone failure'
                }
                success {
                    echo 'Repository clone success'
                }
            }
        }
        
        
        stage('code build') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
