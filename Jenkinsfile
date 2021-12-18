pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
    }
    stages{
        stage("Build"){
            steps{
                sh script: 'mvn clean package'
            }
        }
        stage('Upload war to nexus'){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'simple-app', classifier: '', file: 'target/simple-app-3.0.0-SNAPSHOT.war', type: 'war']], credentialsId: 'nexus-pass', groupId: 'in.javahome', nexusUrl: '172.31.21.164', nexusVersion: 'nexus3', protocol: 'http', repository: 'http://18.117.223.70:8081/repository/simpleapp-release/', version: '3.0.0-SNAPSHOT'
            }
        }
    }
}            