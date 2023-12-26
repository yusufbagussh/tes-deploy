node {
    docker.image('node:20-buster-slim').inside('-p 3000:3000') {
        stage('Build') {
            sh 'npm install'
        }
        stage('Test') {
            sh './jenkins/scripts/test.sh'
        }
        stage('Manual Approve'){
            sh './jenkins/scripts/deliver.sh' 
            input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)' 

        }
        stage('Deploy') {
            sh 'sleep 60'
            sh './jenkins/scripts/kill.sh'
        }
    }
}

// declarative pipeline
// pipeline {
//     agent {
//         docker {
//             image 'node:16-buster-slim' 
//             args '-p 3000:3000' 
//         }
//     }
//     stages {
//         stage('Build') { 
//             steps {
//                 sh 'npm install'
//             }
//         }
//         stage('Test') { 
//             steps {
//                 sh './jenkins/scripts/test.sh' 
//             }
//         }
//         stage('Deploy') { 
//             steps {
//                 sh './jenkins/scripts/deliver.sh' 
//                 input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)' 
//                 sh './jenkins/scripts/kill.sh' 
//             }
//         }
//     }
// }