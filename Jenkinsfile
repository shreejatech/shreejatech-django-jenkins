pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/shreejatech/django-jenkins'
            }
        }
        stage('Setup') {
            steps {
                script {
                    // Create a virtual environment
                    sh 'python -m venv venv'
                    // Activate the virtual environment and install dependencies
                    sh '. venv/bin/activate && pip install -r requirements.txt'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Activate the virtual environment and run tests
                    sh '. venv/bin/activate && python manage.py test'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Add your deployment commands here
                    echo 'Deploying application...'
                    // Example deployment step (replace with your actual deployment command)
                    // sh '. venv/bin/activate && python manage.py migrate'
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            // Add any cleanup commands here if necessary
        }
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
