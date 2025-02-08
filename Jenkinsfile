pipeline {
    agent any

    tools {
        maven "M3"
    }

    stages {
        stage("checkout") {
            steps {
                git branch: "main", url: "https://github.com/vamegah/spring-petclinic.git"
            }
        }

        stage("build") {
            steps {
                bat "mvn compile"
            }
        }

        stage("test") {
            steps {
                bat "mvn test"
            }
        }

        stage("package") {
            steps {
                bat "mvn package"
            }
        }

        stage("deploy") {
            steps {
                bat "/home/coder/.jenkins/workspace/PetClinicDeclarativePipeline/target/*.jar"
            }
        }
    }

    post {
        failure {
            echo "Pipeline failed. Check the logs for details."
        }
        success {
            echo "Pipeline completed successfully."
        }
    }
}
