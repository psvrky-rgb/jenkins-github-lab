pipeline {
    agent any

    stages {
        stage('Checkout Verification') {
            steps {
                echo 'Jenkins has checked out the repository.'
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Build') {
            steps {
                sh '''
                    echo "Building the sample application..."

                    test -f app.sh

                    mkdir -p output

                    echo "Build successful" > output/build.txt

                    cat output/build.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    echo "Testing application files..."

                    test -f app.sh
                    grep -q "Welcome to my sample application" app.sh
                    test -f output/build.txt

                    echo "All tests passed."
                '''
            }
        }
    }

    post {
        success {
            echo 'GitHub Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Review the logs.'
        }
    }
}
