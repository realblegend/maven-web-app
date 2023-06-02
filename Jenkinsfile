node
 {
  
  def mavenHome = tool name: "maven3.9.2"
  
      echo "GitHub BranhName ${env.BRANCH_NAME}"
      echo "Jenkins Job Number ${env.BUILD_NUMBER}"
      echo "Jenkins Node Name ${env.NODE_NAME}"
  
      echo "Jenkins Home ${env.JENKINS_HOME}"
    
      echo "JOB Name ${env.JOB_NAME}"
  

  
  stage("CheckOutCodeGit")
  {
   git branch: 'master2', credentialsId: 'Gitid', url: 'https://github.com/realblegend/maven-web-app.git'
 }
 
 stage("Build")
 {
 sh "${mavenHome}/bin/mvn clean package"
 }
 
/*
 stage("UploadArtifactsintoNexus")
 {
 sh "${mavenHome}/bin/mvn deploy"
 }
 */
  stage("DeployAppTomcat")
 {
  deploy adapters: [tomcat9(credentialsId: '226b4bb7-f7e4-4707-abbb-81f033e9a69e', path: '', url: 'http://35.208.56.74:8089/')], contextPath: null, war: '*/*war'
 }
 
 stage('EmailNotification')
 {
 mail bcc: 'bepapaul65@gmail.com', body: '''Build is over

 Thanks,
 Mithun Technologies,
 9980923226.''', cc: 'bepapaul65@gmail.com', from: '', replyTo: '', subject: 'Build is over!!', to: 'bepanovak@gmail.com'
 }
 
 
 }
