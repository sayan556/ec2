def remote = [:]
remote.name = 'test'
remote.host = '3.238.194.4'
remote.port = 22
remote.allowAnyHosts = true


pipeline {
agent any

   stages {
     stage('Git Clone') {
       steps {
// Get some code from a GitHub repository
           git branch: 'main', credentialsId: '5a22a18e-6011-429e-971f-9cb1d3b24d20', url: 'https://github.com/sayan556/ec2.git'
         }
       }
     stage('Deployment'){
       steps {
          script {
// move the new changed
               withCredentials([usernamePassword(credentialsId: 'ec2sshcred', passwordVariable: 'pass', usernameVariable: 'user')]) {
               remote.user = user
               remote.password = pass
               sshPut remote: remote, from: "index.html", into: "/var/www/html"
                  }
               }
           }
      }
}
