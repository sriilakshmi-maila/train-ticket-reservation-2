\# Train Ticket Reservation – CI/CD Automation Using AWS



\## Project Overview



This project demonstrates an automated CI/CD pipeline for an existing Java-based Train Ticket Reservation application using GitHub Actions, Docker, Amazon ECR, and Amazon ECS.



The objective is to automate the application build, Docker image creation, image delivery to Amazon ECR, and deployment to Amazon ECS Fargate whenever code is pushed to the `master` branch.



\## My Contribution



I implemented and configured the CI/CD workflow for the existing application.



* &#x20;Configured a GitHub Actions self-hosted runner on an Amazon EC2 instance.
* &#x20;Created a GitHub Actions workflow triggered by pushes to the `master` branch.
* &#x20;Configured Java 17 and Maven to build the application.
* &#x20;Automated Docker image creation using the project Dockerfile.
* &#x20;Configured authentication with AWS using GitHub Actions Secrets.
* &#x20;Automated Docker image tagging and pushing to Amazon ECR.
* &#x20;Configured the workflow to update the ECS task definition with the latest image URI.
* &#x20;Automated deployment to an existing Amazon ECS Fargate service.



The Java application and AWS deployment resources were provided as the starting environment. My focus was implementing the CI/CD automation.



\## Architecture



GitHub Repository  

↓  

GitHub Actions Workflow  

↓  

Self-hosted Runner on Amazon EC2  

↓  

Maven Build  

↓  

Docker Image Build  

↓  

Amazon ECR  

↓  

ECS Task Definition Update  

↓  

Amazon ECS Fargate Deployment



\## Technologies Used



* &#x20;AWS: EC2, IAM, Amazon ECR, Amazon ECS Fargate
* &#x20;CI/CD: GitHub Actions
* &#x20;Build Tool: Maven
* &#x20;Containerization: Docker
* &#x20;Application: Java, Maven WAR packaging
* &#x20;Operating System: Linux (self-hosted runner)



\## CI/CD Workflow



1. &#x20;A developer pushes code to the `master` branch.
2. &#x20;GitHub Actions triggers the CI/CD workflow.
3. &#x20;The job runs on the self-hosted runner hosted on EC2.
4. &#x20;GitHub Actions checks out the repository.
5. &#x20;Maven builds the application and generates a WAR artifact.
6. &#x20;Docker builds an image using the Dockerfile.
7. &#x20;The workflow authenticates with Amazon ECR.
8. &#x20;The Docker image is tagged and pushed to the ECR repository.
9. &#x20;The updated task definition is deployed to the existing ECS service.
10. &#x20;The workflow waits for the ECS service to reach a stable state.



\## Repository Structure





train-ticket-reservation-2/

│

├── .github/

│   └── workflows/

│       └── java-cicd.yml

│

├── src/

│

├── WebContent/

│

├── Dockerfile

├── pom.xml

├── task-definition.json

└── README.md



\## GitHub Actions Secrets



The workflow uses GitHub Actions Secrets for AWS authentication:



* AWS\_ACCESS\_KEY\_ID
* AWS\_SECRET\_ACCESS\_KEY
* AWS\_ACCOUNT\_ID



Sensitive AWS credentials are stored in GitHub repository secrets rather than hardcoded in the workflow.



\## Run the Maven Build Locally



mvn clean package -DskipTests



\## Docker Image Build



docker build -t demo-repo:latest .



\## Key Learning Outcomes



\- Implementing a CI/CD pipeline using GitHub Actions.

\- Configuring and using a self-hosted GitHub Actions runner on EC2.

\- Automating Maven application builds.

\- Packaging applications into Docker images.

\- Publishing container images to Amazon ECR.

\- Understanding ECS task definition updates and Fargate deployments.

\- Managing AWS credentials through GitHub Actions Secrets.

\- Understanding the end-to-end application delivery process.



\## Future Improvements



\- Use AWS IAM OIDC authentication instead of long-lived access keys.

\- Use unique Docker image tags instead of relying only on `latest`.

\- Add automated testing and code-quality checks.

\- Improve deployment monitoring and rollback handling.





