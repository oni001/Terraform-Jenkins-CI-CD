pipeline {
    agent {
        node {
            label 'build-terraform-aws'
        }
    }

    stages {

        stage('terraform clone') {
            steps {
                sh 'git pull git@github.XXXX.com:repo/terraform.git'
            }     
        }
        stage('terraform init') {
            steps {
                sh 'cd /jenkins-agent/workspace/terraform_deploy_dev/fbs_tf/envs/test ; /home/jenkins/.terraform.versions/terraform_0.12.20 init'
            }
        }
        stage('terraform plan') {
            steps {
                sh 'cd /jenkins-agent/workspace/terraform_deploy_dev/fbs_tf/envs/test ; /home/jenkins/.terraform.versions/terraform_0.12.20 plan'
            }
        }    
        stage('terraform apply') {
            steps {
                input "Would you like to apply?"
                sh 'cd /jenkins-agent/workspace/terraform_deploy_dev/fbs_tf/envs/test ; /home/jenkins/.terraform.versions/terraform_0.12.20 apply -auto-approve'
            }
        }
    }
}
