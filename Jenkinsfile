pipeline{
 agent any 
 stages{
  stage('SCM'){
    steps {
      git 'https://github.com/thunikipatla/Docker_build.git'
    }
  }
  stage('Copy-Artifact-upstream'){
    steps{
      copyArtifacts filter: 'webapp/target/openmrs.war', fingerprintArtifacts: true, projectName: 'openmrs-build', selector: lastWithArtifacts()
    }
  }
  stage('Deploy'){
  steps{
    sh ''' docker build -t openmrs . '''
  }
  }
 }
}
