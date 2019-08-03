pipeline {
  agent any
  stages {
	  	stage('Build') { 
	      steps { 
	        sh "'C:\Program Files\apache-maven-3.6.1\bin\mvn' clean package --settings 'C:\Program Files\apache-maven-3.6.1\conf\settings.xml' -P foo"
	      }
	    }
	    stage('Unit Test') { 
	      steps {
	        sh "'C:\Program Files\apache-maven-3.6.1\bin\mvn' clean test"
	      }
	    }
	    stage('Deploy CloudHub') { 
		      environment {
		        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
		      }
		      steps {
		        sh "'C:\Program Files\apache-maven-3.6.1\bin\mvn' deploy -P cloudhub -Dmule.version=3.9.0 -Dcloudhub.username=${ANYPOINT_CREDENTIALS_USR} -Dcloudhub.password=${ANYPOINT_CREDENTIALS_PSW} -Dcloudhub.env=Development" 
		      }
	    }
  	}
}
