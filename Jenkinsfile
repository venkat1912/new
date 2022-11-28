node {
    stage('git checkout') {
    git 'https://github.com/venkat1912/maven.git'
}
    stage('Build') {
    sh 'mvn clean install'
}
    stage('deploying on tomcat-server') {
    deploy adapters: [tomcat9(credentialsId: 'Tomcat_credintials', path: '', url: 'http://3.136.116.107:8080/manager/html')], contextPath: 'kiran', war: '**/*.war'
}
    stage('continuous testing') {
    git 'https://github.com/venkat1912/FunctionalTesting.git'
}
    stage('continuous delivery on prod-server') {
        input message: 'waiting for approval from delivery', submitter: 'naga'
    deploy adapters: [tomcat9(credentialsId: 'Prod-Tomcat_credintials', path: '', url: 'http://3.142.209.247:8080/manager/html')], contextPath: 'KiranF', war: '**/*.war'
}
}
