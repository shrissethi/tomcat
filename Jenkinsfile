pipeline {
   agent any

   tools {
      // Install the Maven version configured as "M3" and add it to the path. Demo comment
      maven "maven"
      jdk "java"
                
   }

   stages {
      stage('Checkout') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/shrissethi/tomcat.git'   
         }

      }
      
      
      stage('Testing') {
         steps {
           
            // To run Maven on a Windows agent, use
           bat "mvn test"
         }
      }
         
          stage('Build') {
         steps {
           
            // To run Maven on a Windows agent, use
           bat "mvn package"
         }

      }
      
      stage('Deploy') {
         steps {
        
            // To run Maven on a Windows agent, use
           bat label: '', script: 'copy /Y target\\test-1.0.war E:\\DevOps\\Tomcat\\webapps'
         }

      }
      stage ('Notify')
      { steps{
            //Send notification mail after successful deployment
           mail bcc: '', body: '''Hello,


Your build has got executed successfully


Regards,
Team Jenkins''', cc: '', from: '', replyTo: '', subject: 'Jenkins Mail', to: 'shrissethi@gmail.com' 
      }
      }
   }
}
