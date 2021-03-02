pipeline {
	agent any  
	stages {
		stage("Pull Latest Image") {
			steps {
				sh "docker pull silver3456/upgrade-selenium-docker"
			}
		}

		stage("Start Grid") {
			steps {
				sh "docker-compose up --build -d hub chrome"
			}
		}
		stage("Run Test") {
			steps {
				sh "docker-compose up --build loan-application"
			}
		}
	}
	
	post {
		always {
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"
		}
	}
}