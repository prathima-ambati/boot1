pipeline {
   agent any
   tools {
      jdk 'JAVA_HOME'
      maven 'MAVEN_HOME'
    }
    stages{
       stage('Build'){
          steps {
                sh 'mvn clean package'       
                sh "docker build -t webapp:${env.BUILD_ID} ."                
                sh 'docker login -u prathimaambati -p Ganapathi@570'
                sh "echo prathima"
                sh "docker tag webapp:${env.BUILD_ID} prathimaambati/webapp:${env.BUILD_ID}"                
                sh "docker push prathimaambati/webapp:${env.BUILD_ID}"
          }
       }
       stage('Run Container on Jenkins Server'){
          steps {
               sh 'docker login -u prathimaambati -p Ganapathi@570'
               sh "docker run -p 8084:8080 -d --name my-apll prathimaambati/webapp:${env.BUILD_ID}"
          }
    }
 }
}
