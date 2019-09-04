pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                bash 'npm install'
            }
        }
        stage('Test') {
            steps {
                bash '.simple-node-js-react-npm-app/jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                bash '.simple-node-js-react-npm-app/jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                bash '.simple-node-js-react-npm-app/jenkins/scripts/kill.sh'
            }
        }
    }
}
