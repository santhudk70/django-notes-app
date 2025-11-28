pipeline {
    agent { label 'vinod' }

    libraries {
        lib('Shared')
    }

    stages {
        stage('Hello') {
            steps {
                script {
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                clone("https://github.com/santhudk70/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                
                docker_build("notes-app","latest","santhoshdk031989")
            }
        }
        stage("Push to Dockerhub"){
            steps{
                script{
                    docker_push("notes-app","latest","santhoshdk031989")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is a Deploying the Code"
                sh "docker compose up -d"
            }
        }
    }
}
