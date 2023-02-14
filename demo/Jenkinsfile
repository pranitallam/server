pipeline {
    agent any
    tools {
        maven "Maven"
       
    }
    stages {
        stage('Initialize'){
            steps{
                echo "PATH = ${M2_HOME}/bin:${PATH}"
                echo "M2_HOME = /opt/maven"
            }
        }
        stage('Build') {
            steps {
                dir('demo'){
                sh 'mvn -B -DskipTests clean package'
                }
            }
       }
        stage('Test') {
            steps {
                dir('demo'){
                sh 'mvn test'
                }
            }
       }
        stage('Install') {
            steps {
                dir('demo'){
                sh 'mvn -B -DskipTests clean install'
                }
            }
       }
        stage('Sonar Scan'){
		    steps{
			    dir('springboottest'){
			    withSonarQubeEnv('sonarqube'){
		        sh 'mvn sonar:sonar'
		 }
	    }
	 }
	 }
    }
}
