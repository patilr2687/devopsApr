node {
   stage('Preparation') { 
   git 'https://github.com/patilr2687/devopsApr.git'
   }
   stage('Build')
   {
   def mvnHome= tool 'M2_HOME'
   withEnv(["MVN_HOME=$mvnHome"]){
   sh '"$MVN_HOME/bin/mvn" clean install compile package'
     }
   }
   stage ('Deploy'){
   
   deploy adapters: [tomcat9(credentialsId: 'bc0354ca-7013-4514-b775-bbd0b321d626', path: '', url: 'http://192.168.0.9:9080')], contextPath: null, war: '**/*.war'
   
   }  
   stage('Notificatiom'){
   emailext attachLog: true, body: 'Please find your project status.', subject: 'Jenkins Pipeline Build', to: 'rahul.p2611@gmail.com'
   }
   stage('Print'){
  sh 'echo "The Devops pipeline project is sucessfully deploy"' 
   }
  }
