node {
    def app

    stage('Clone repository') {
        /* repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* To builds the dockerimage */
        //update your ECR registry URI
        app = docker.build("544557330409.dkr.ecr.ap-south-1.amazonaws.com/sesispin2")
    }

    stage('Test image') {
        /* Try killing some white walkers for testing ;-) */

        app.inside {
            sh 'echo "Hurray !! Tests passed., Valar Morghulis "'
        }
    }

    stage('Push image') {
        /* Finally, we'll push the image */
        //docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
        // update your ECR registry URI and jenkins crendential paramater
        docker.withRegistry('https://544557330409.dkr.ecr.ap-south-1.amazonaws.com', 'ecr:us-east-1:aws')    {
            //app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
