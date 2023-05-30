pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                echo 'Tested Successfully'
            }
        }
        stage('Trigger ManifestUpdate') {
                echo "triggering updatemanifestjob"
                build job: 'gitops', parameters: [string(name: 'DOCKERTAG', value: env.BUILD_NUMBER)]
        }
    }
}
