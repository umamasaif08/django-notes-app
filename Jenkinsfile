```groovy
@Library("shared") _

pipeline {
    agent any

    stages {

        stage("Hello") {
            steps {
                script {
                    bat "hello"
                    hello()
                }
            }
        }

        stage("Code Clone") {
            steps {
                script {
                    clone(
                        "https://github.com/umamasaif08/django-notes-app.git",
                        "main"
                    )
                }
            }
        }

        stage("Code Build & Test") {
            steps {
                script {
                    docker_build(
                        "notes-app",
                        "latest",
                        "umamasyf"
                    )
                }
            }
        }

        stage("Push To DockerHub") {
            steps {
                script {
                    docker_push(
                        "dockerHubCred",
                        "latest",
                        "notes-app",
                        "umamasyf"
                    )
                }
            }
        }

        stage("Deploy") {
            steps {
                bat "docker compose down"
                bat "docker compose up -d --build"

            }
        }
    }
}
```

