pipeline {
  agent any

  tools
  {
    maven "Maven"
  }

  stages {
    stage ('checkout') {
      steps{
        git branch: 'master' , url: 'https://github.com/tarigelnil/CI-CD-DeploymentUsingAnsibleCMTool'
      }
    }
    stage ('Tools init'){
      steps{
        scripts{
          echo "PATH = $(PATH)"
          echo "M2_HOME = $(M2_HOME)"
          def tfHome = tool name:'Ansible'
            env.PATH = "$(tfHome) : $(env.PATH)"
             sh 'ansible --version'
        }
      }
    }
    stage('execute Maven'){
      steps{
        sh 'mvn package'
      }
    }
    stage('Ansible deploy'){
      steps{
        sh "ansible-playbook mainPlaybook.yaml"
      }
    }
 }
}
