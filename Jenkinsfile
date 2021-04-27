node('master') {
    stage('ContinuousDownload') {
    git 'https://github.com/intelliqittrainings/maven.git'
}
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'c105f7f0-5a5e-40df-9a3f-699a30a466b3', path: '', url: 'http://172.31.19.113:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
      git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
      sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContinuousDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: '5adf625a-233a-4204-b1d0-e85042398745', path: '', url: 'http://172.31.28.103:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
