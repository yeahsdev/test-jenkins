pipeline {
  agent {
    label "jenkins-node"
  }


  triggers {
    pollSCM('* * * * *')
  }


  stages {
    stage('Checkout') {
      steps {
        git branch: 'main',
        url: 'https://github.com/yeahsdev/source-maven-java-spring-hello-webapp'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Deploy') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'tomcat', url: 'http://192.168.176.136:8080')], contextPath: null, war: 'target/hello-world.war'
      }
    }
  }
}
