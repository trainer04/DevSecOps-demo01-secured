# DevSecOps-demo01

## For Linux:

1. Check partition size (setup > 20 Gb if necessary)  
`df -h`

2. Install Java 21  
`sudo apt install openjdk-21-jdk`

3. Install Docker  
According [instructions](https://docs.docker.com/engine/install/)

4. Setup local repo for Docker:  
`sudo docker run -d -p 5000:5000 --restart=always --name local-registry registry:2`

5. Install Jenkins  
According [instructions](https://www.jenkins.io/doc/book/installing/)

6. Add user `jenkins` to the `docker` group  
`sudo usermod -a -G docker jenkins`  
then restart server to apply the changes

7. Setup Jenkins configuration  
a. Unblock Jenkins with `https://<ip>:8080`  
`sudo cat /var/lib/jenkins/secrets/initialAdminPassword`  
b. Install suggested plugins  
c. Add the "Docker Pipeline" plugin  
d. Create Pipeline:  
- Select "New Item" - "`Pipeline`"
- Set "Name" ("`Demo`" or something)
- Set "GitHub project" with an URL to the project (like "https://github.com/trainer04/DevSecOps-demo01.git")
- Set "Definition" with "`Pipeline script from SCM`"
- Set "SCM" as "`Git`"
- Set "Repository URL" with your URL (like "https://github.com/trainer04/DevSecOps-demo01.git")
- Set credentials if necessary (for private repos)
- Set "Branch Specifier" as "`*/main`"
- Set "Script Path" with the path to the Jenkins file (like "`spring-boot-app/JenkinsFile`")
- Save the item