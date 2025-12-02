Maven - java
open eclipse ide
launch your workspace(any location)
step 1: create a new maven pro
File --> New --> Other.. --> Expand Maven --> Select maven project --> next
Step 2 : Project config 
Click next for (loc)
Let catalog default 
Filter search org.apache.maven --> choose (artifactid) quickstart type
Step 3 : . Define Project Metadata
    Group ID: (e.g., com.example)
    Artifact ID: (e.g., my-maven-project)
    Version: (default is usually fine)
    Click "Finish"
In Console, artifacts are grouped. When prompted with Y/N, type 'Y'.
Step 4 : Maven Project Created
    Project structure is generated with a standard Maven layout
     Includes:
        src/main/java (for Java source code)
        src/test/java (for test code)
        pom.xml (Maven configuration file)
Step 5:Update Project Settings (if needed)
    Right-click on the project -> Maven -> Update Project...
     Ensure dependencies are up to date
Step 6:Build and Run Maven Project
    Right-click on App.java -> Run As -> Maven Clean
(app.java is present under src/main/java)
Step 7:Right-click on App.java -> Run As -> Maven Install
Step 8:Right-click on App.java -> Run As -> Maven Test
└Step 9: Right-click on App.java -> Run As -> Maven Build
A configuration set up opens up-->
Goals : clean install test 
Click on run.
Step 10 : check console for SUCCESS Message
Step 11:Run the application
     Right-click on App.java -> Run As -> Java Application
Output: "Hello World" displayed in the console.


Maven WEB JAVA Project
Step 1: Open Eclipse
   └── 1.1 Launch Eclipse IDE.
   └── 1.2 Select or create a workspace.
Step 2: Create a New Maven Project
   └── 2.1. File -> New -> Project...
       └── 2.1.1. Expand "Maven"
       └── 2.1.2. Select "Maven Project" and click "Next"
Step 3: Choose Maven Archetype
   └── 3.1. Select an archetype(e.g "'org.apache.maven.archetypes' -> 'maven-archetype-webapp' 1.4 ")
   └── 3.2. Click "Next"
Step 4: Configure the Maven Project
   └── 4.1 Group Id: Enter a group ID (e.g., com.example).
   └── 4.2 Artifact Id: Enter an artifact ID (e.g., my-web-app).
   └── 4.3 Click **Finish** to create the project.
**If any error in index.jsp file (webapp/src/main/webapp/index.jsp) **
Go to browser -> Open mvnrepository.com
 Search for 'Java Servlet API' -> Select the latest version.
 Copy the dependency code -> Paste it in MavenWeb’s pom.xml under the target folder
       └── Example:
           ```xml
           <dependency>
               <groupId>javax.servlet</groupId>
               <artifactId>javax.servlet-api</artifactId>
               <version>4.0.1</version>
               <scope>provided</scope>
           </dependency>
           ```
   Step 6:-. Configure server:
    └── Window -> Show View -> Servers
    └── Add server -> Select Tomcat v9.0 server -> Click Next
    └── Configure server options (e.g., ports, server location).
Step 7:-. Modify 'tomcat-users.xml':
    └── Add role and user details under <tomcat-users> tag.
Step 8:. Build the project:
    └── Right-click on index.jsp -> Run As -> Maven Clean
    └── Right-click on index.jsp -> Run As -> Maven Install
    └── Right-click on index.jsp -> Run As -> Maven Test
    └── Right-click on index.jsp -> Run As -> Maven Build
Step 9. In the Maven Build dialog:
    └── Enter Goals: clean install test
    └── Click on Apply -> Click on Run
Step 10. Check console for BUILD SUCCESS message.
Step 11. Run the application:
    └── Right-click on index.jsp -> Run As -> Run on Server
    └── Select the Tomcat server -> Click on Finish
Step 12. Output: "Hello World" webpage displayed.
(If you want to push this to your git hub)
1. Create repo in git
2. In git bash in eclipse itself 
git init
git remote add origin <git_repo_url>
git add .
git commit -m "first commit"
git branch -M main or master as per your repo..
git push -u origin main
**IF they just want you to perform few commands**
1.git version //gives version
2.git config --global user.name "your_name"
3.git config --global user.email "your_email"
4. git clone <url> // to create a copy of existing repo
5. git remote remove <remote name (like eg:origin)>
6. git remote rename <oldname> <newname>
7. git fetch <remotename> // fetch updates from remote repo
8. git status //shows status of changes in working dir and staging area
9. git add . //adds changes 
10. git branch //lists all branches 
    git branch branch-name //with name
    git branch -d <branch_name> //deletes
11. git checkout branch-name //to switch to diff branch
    git checkout -b new-branch // to create and switch 
12.merge --> merges specified branch into current branch (changes from feature branch to main branch)
   git checkout main //switch to main
   git merge branch-name //merges branch-name into main
13. git reset file //removes that file from staging area but leaves dir unchanged
14. git revert <commit> //creates new commit that undoes changes 
15. git log //view history
16. git diff // displays diff btw various commits and statging area
17. git restore filename // to undo changes made to file before staging.


PART 1 — Install & Open Jenkins
1.	Open your browser.
2.	Type: http://localhost:8080
You will see the Jenkins dashboard.
________________________________________
 PART 2 — Create Maven Java Build Job (MavenJava_Build)
1️ Click “New Item”
•	Left side → first option, 
2️ Give a name
Example:
MavenJava_Build
Select:
Freestyle Project
Click OK.
________________________________________
3️ Fill Project Details
Inside Configuration page:
Description:
Java Build demo
________________________________________
4️ Add GitHub Code
Scroll to:
✔ Source Code Management → Choose Git
You will see a box:
Repository URL
Paste your Maven Java GitHub link here (example):
https://github.com/someone/maven-java-demo.git
________________________________________
5️ Build Steps (Very Important)
Scroll to Build section → click:
▶ Add Build Step → Invoke top-level Maven targets
You will now add 2 steps:
STEP A
•	Maven version: select your configured Maven (example: MAVEN_HOME)
•	Goals: clean
STEP B (again click “Add Build Step”)
•	Goals: install
________________________________________
6️ Post-Build Actions
Scroll down → Click:
▶ Add post-build action → Archive the artifacts
Files to archive: **/*
Then again:
▶ Add post-build action → Build other projects
Enter: MavenJava_Test
Choose:
•	Trigger only if build is stable
7️ Save the job
Click Save at bottom.
________________________________________
 PART 3 — Create MavenJava_Test Job
1️ Click “New Item”
Name: MavenJava_Test
Select Freestyle → OK.
________________________________________
2️ Description
Test demo
________________________________________
3️ Build Environment
Scroll → tick:
✔ Delete workspace before build starts
Why?
It removes old files so test always runs fresh.
________________________________________
4️ Copy the build output from previous job
Build Steps → Add Build Step → Copy artifacts from another project.
Fill:
•	Project name → MavenJava_Build
•	Build → Stable build only
•	Artifacts to copy: **/*
________________________________________
5️ Add Test Step
Add Build Step → Invoke top-level Maven targets
•	Goals: test
________________________________________
6️ Archive test results
Add Post Build Action → Archive artifacts
Files: **/*
Click Save
________________________________________
PART 4 — Create Pipeline View
Steps:
1.	On Jenkins dashboard, click “+” beside “All”
2.	Name: MavenJava_Pipeline
3.	Select: Build Pipeline View
4.	Pipeline flow:
o	Initial job → MavenJava_Build
5.	Save.
________________________________________
PART 5 — Run
1.	Open pipeline view
2.	Click “Run”
3.	Green = success
4.	Click boxes → open console
________________________________________
 Maven Java part DONE!
________________________________________
PART 6 — Repeat SAME for Maven Web Project
You will create 3 jobs:
1.	MavenWeb_Build
2.	MavenWeb_Test
3.	MavenWeb_Deploy
And pipeline.
The steps are exactly same as Java — except the deploy job:
In MavenWeb_Deploy:
•	Copy artifacts from test job
•	Add Post-build Action → Deploy WAR/EAR to container
•	WAR file: **/*.war
•	Add Tomcat 9 remote server
o	username: admin
o	password: 1234
o	URL: http://localhost:8085/
Done.
________________________________________
WEEK 9 — Scripted Pipeline (BEGINNER VERSION)
Goal: Create ONE Jenkins job using Pipeline script.
________________________________________
Click “New Item”
Name: ScriptedPipeline
Choose: Pipeline
Click OK.
________________________________________
 Scroll down to Pipeline section
Under Definition, select:
Pipeline script
________________________________________
Paste the script

pipeline {
    agent any
    tools{
        jdk 'JAVA_HOME'
        maven 'MAVEN_HOME'
    }
    stages {
        stage('git repo & clean') {
            steps {
                deleteDir()
                git url: 'https://github.com/Tusshar-K/MavenWeb_Build_forPractice.git', branch: 'main'
                bat "mvn clean -f pom.xml"
            }
        }
        stage('install') {
            steps {
                bat "mvn install -f pom.xml"
            }
        }
        stage('test') {
            steps {
                bat "mvn test -f pom.xml"
            }
        }
        stage('package') {
            steps {
                bat "mvn package -f pom.xml"
            }
        }
    }
}
Change:
git clone <paste your GitHub URL>
And change “mavenjava” to your folder name if needed.
________________________________________
Save
________________________________________
Run
Click Build now.
Take screenshots of:
•	Build stages
•	Console output
Done.
________________________________________
WEEK 10 — Minikube, Kubernetes, Nagios, AWS (BEGINNER VERSION)
________________________________________
PART 1 — Minikube
Start Minikube
Open CMD or PowerShell:
minikube start
2️⃣ Create an nginx server
kubectl create deployment mynginx --image=nginx
Check:
kubectl get pods
3️⃣ Expose the deployment
kubectl expose deployment mynginx --type=NodePort --port=80
4️⃣ Scale to 4 pods
kubectl scale deployment myapp --replicas=4
->Port forwarding: kubectl port-forward svc/myapp 8081:80
8081 can be replaced by any
->Kubernets dashboard 
Minikube dashboard
->Stopping
kubectl delete deployment mynginx
kubectl delete service mynginx
minikube stop
________________________________________
PART 2 — Nagios in Docker
 Pull image
docker pull jasonrivers/nagios
Run Nagios
docker run --name nagiosdemo -p 8888:80 jasonrivers/nagios
Open browser
Go to:
http://localhost:8888
Login:
•	username: nagiosadmin
•	password: nagios
________________________________________
EEK 11 — GitHub Webhook 
________________________________________
PART 1 — Install ngrok
Run in CMD:
ngrok http 8080
You will see:
https://abc123.ngrok.io (just for example)
Copy this.
________________________________________
PART 2 — Add Webhook in GitHub
1.	Open your GitHub repo → Settings → Webhooks
2.	Click Add Webhook
3.	Payload URL:
https://abc123.ngrok.io/github-webhook/ (make sure to add /github-webhook/ at the end of your ngrok url)
4.	Content type: application/json
5.	Events: ✔ Just the push event
6.	Add webhook
________________________________________
PART 3 — Configure Jenkins job
Open your job → Configure → Build Triggers
✔ Tick: GitHub hook trigger for GITScm polling
Save.
________________________________________
PART 4 — Test webhook
1.	Make any change to your GitHub project
2.	Push the code
3.	Jenkins WILL automatically start building
DONE.
WEEK 12 — Deploying App in AWS EC2 Using Docker
________________________________________
PART 1 — Create EC2 instance
1.	AWS → Start Lab and click on the green-dot → EC2 → Launch Instance
2.	Name: ubuntu
3.	AMI: Ubuntu Server 22.04 LTS (Free tier)
4.	Instance type: t2.micro
5.	Create new key pair → download .pem file
6.	Security group:
✔ SSH (22)
✔ HTTP (80)
7.	Launch instance.
________________________________________
PART 2 — Connect to EC2
Go to instance → Click Connect → SSH tab
Copy:
ssh -i "your-key.pem" ubuntu@<your-public-ip>
Paste into PowerShell.
You are now inside your remote Ubuntu machine.
________________________________________
PART 3 — Install 
Run:
sudo apt update
sudo apt-get install docker.io
sudo apt install git
sudo apt install nano
________________________________________
Create a html file and push into git or what ever is given 
PART 4 — Clone your project
git clone <your GitHub link>
cd <project folder>
________________________________________
PART 5 — Create Dockerfile
Run:
nano Dockerfile
Paste:
FROM nginx:alpine
COPY . /usr/share/nginx/html
(For maven WEB project)-> docker file code 
FROM tomcat:9-jdk11
COPY target/*.war/usr/local/tomcat/webapps
Save:
•	CTRL + O → Enter
•	CTRL + X
________________________________________
PART 6 — Build Docker image
sudo docker build -t mywebapp .
________________________________________
PART 7 — Run the container
sudo docker run -d -p 80:80 mywebapp
________________________________________
PART 8 — Open your website
Copy your EC2 public IP
Paste in browser → Your website appears 🎉
->Stopping 
sudo docker ps -> gives container id 
sudo docker stop <container id>

