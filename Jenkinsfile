pipeline {
    agent any
     
     environment {
        jenkins_webhook = "https://qualitiasoftware.webhook.office.com/webhookb2/46a50307-4e61-4323-8015-0ecc393ce24d@6eccc19d-c8e1-43c4-a2f6-03ca7c78d7cb/IncomingWebhook/0263867867b24902b93a0c39042a8b16/a9a4fbff-87ba-4624-883f-1284eff05941"
    }


    stages {
        stage('hello') {
            steps {
                echo 'hello'
            }
        }
        stage('Build') {
            steps {
                echo 'Building jobs'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying Jobs'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing Jobs'
            }
        }
        stage('Release') {
            steps {
                script
                {
                    if(currentBuild.result=="SUCCESS")
                    {
                        branchName = branchName.replace("/","\\")
						office365ConnectorSend message: "The ${AGENT} build is available at ${branchName}\\${env.Version}.${env.BUILD_NUMBER} \n\n  ", status:"Success", webhookUrl:"${jenkins_webhook}"
                    }
                }          
            }
        }
    }
}
