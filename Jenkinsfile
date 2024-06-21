pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/vinayakyadav27/chatbot.git', branch: 'master')
      }
    }

    stage('Log') {
      steps {
        sh 'whoami'
      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f albertsons-frontend/Dockerfile -t vinayakyadav4017/jenkins-front:latest .'
      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'vinayakyadav4017'
        DOCKERHUB_PASSWORD = 'Qwertyuiop@4017'
      }
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('Push') {
      steps {
        sh 'docker push vinayakyadav4017/curriculum-front:latest'
      }
    }

  }
}