pipeline {
    agent any
triggers {
        cron('H */2 * * 1-5')
    }
 environment {
        CC = "google.com"
    }
    parameters {
	string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
	}
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'echo url=${CC}'
                echo "hello ${params.PERSON}"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'date'
            }
        }
        stage('Deploy') {
            input {
                            message "Should we continue?"
                            ok "Yes, we should."
                            submitter "alice,bob"
                            parameters {
                                string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                            }
                        }
                        steps {
                            echo "Hello, ${PERSON}, nice to meet you."
                        }
        }
    }
 	    post {
            always {
                echo 'I will always say Hello again!'
            }
        }
}