node{
    
    def mavenHome = tool name: 'maven3.8.5'
    
    echo "The Job Name is: ${env.JOB_NAME}"
    echo "The Build Number is: ${env.BUILD_NUMBER}"
    echo "The Node Name is: ${env.NODE_NAME}"
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
   
    //Checkout Code State
    stage('CheckoutCode'){
    git branch: 'development', credentialsId: '86c7009a-0258-49f1-9c98-089c41ef1e4c', url: 'https://github.com/sivaramreddyp/maven-web-application.git'    
    }
    
     //Build
    stage('Build'){
    sh "${mavenHome}/bin/mvn clean package"
    }
  
  /*
    //Execute SonarQube Report
    stage('ExecuteSOnarQubeReport'){
    sh "${mavenHome}/bin/mvn sonar:sonar"
    }
    
    //UploadArifacts Into Nexus
    stage('UploadArtifactsIntoNexus'){
    sh "${mavenHome}/bin/mvn deploy"
    }
    
    //Deploy App into Tomcat Server
    stage('DeployApp'){
    sshagent(['08fd3be9-397b-4a6c-931c-00c7968c63a2']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.36.110:/opt/apache-tomcat-9.0.68/webapps"
    }
    }    
   
   */
}//node closing
