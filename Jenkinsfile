pipeline {
    agent  { label 'JDK-11' }
    stages {
        stage('vcs') {
            steps {
                git branch: 'REL_INT_1.0', url: 'https://github.com/satishnamgadda/spring-framework-petclinic.git'
            }

        }
        stage('build') {
            steps {
                sh '/usr/share/maven/bin/mvn package'
            }
        }
        stage('artifacts') {
            steps {
            archiveArtifacts artifacts: '*/target/*.jar', followSymlinks: false
            }
        }
        stage('archive results') {
            steps {
                junit '**/surefire-reports/*.xml'
            }
        }
    }
    
}