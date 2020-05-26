pipeline {
  agent any
  options {
    // Stop the build early in case of compile or test failures
    skipStagesAfterUnstable()
  }
    stages{
        stage('Clean'){
            steps{
                sh './gradlew clean'
            }
        }
        stage('Compile') {
            steps {
            // Compile the app and its dependencies
                sh './gradlew compileDebugSources'
            }
        }
        stage('Build APK') {
            steps {
              // Finish building and packaging the APK
              sh './gradlew assembleDebug'

              // Archive the APKs so that they can be downloaded from Jenkins
              archiveArtifacts '*/.apk'
            }
        }
    }
}