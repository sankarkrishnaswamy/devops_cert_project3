pipeline {

  environment {

    registry = "krishnaswamy/devops_cert_project3"

    registryCredential = 'dockerhub'

  }

  agent any

  stages {

        stage('Building image') {

        steps{

            script {

            dockerImage = docker.build registry + ":$BUILD_NUMBER"

            }

        }

        }



        stage('Deploy Image') {

        steps{

            script {

            docker.withRegistry( '', 'dockerhub' ) {

                dockerImage.push()

            }

            }

        }

        }



        stage('Remove Image') {

        steps{

            sh "docker rmi $registry:$BUILD_NUMBER"

        }

        }

   }   

}



node {

    stage('Execute Image'){

        def customImage = docker.build("krishnaswamy/devops_cert_project3:${env.BUILD_NUMBER}")


