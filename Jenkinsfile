pipeline {
  agent {
    label 'ubuntu-1804 && amd64 && overlay2'
  }
  stages {
    stage('Build result') {
      steps {
        sh 'docker build -t dockersamples/result ./result'
      }
    }
    stage('Build vote') {
      steps {
        sh 'docker build -t dockersamples/vote ./vote'
      }
    }
    stage('Build worker') {
      steps {
        sh 'docker build -t dockersamples/worker ./worker'
      }
    }
    stage('Push result image') {
      steps {
        docker.withRegistry('https://index.docker.io/v1/', 'dockerbuildbot-index.docker.io') {
          sh 'docker push dockersamples/result'
        }
      }
    }
    stage('Push vote image') {
      steps {
        docker.withRegistry('https://index.docker.io/v1/', 'dockerbuildbot-index.docker.io') {
          sh 'docker push dockersamples/vote'
        }
      }
    }
    stage('Push worker image') {
      steps {
        docker.withRegistry('https://index.docker.io/v1/', 'dockerbuildbot-index.docker.io') {
          sh 'docker push dockersamples/worker'
        }
      }
    }
  }
}
