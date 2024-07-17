pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('Test') {
            steps {
            echo 'Testing if robots.txt exists on build folder'
            sh '''
                test -f build/robots.txt
            '''
            echo 'running "npm test"'
            sh '''
                npm test
            '''
            }
            
        }
    }
}

