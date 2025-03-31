# PostmanTesting 


### What is POSTMAN?
Postman is a Google Chrome app for interacting with HTTP APIs. It presents you with **a friendly GUI for constructing requests and reading responses**. It works on the backend, and makes sure that each API is working as intended.<br>
**It is an API client.
Develop, Test(Manual & Automated), Share & Document APIs.**
Postman is the way to streamline the process of API testing.<br> Download Postman for your OS: https://www.postman.com/downloads/

<img src="https://github.com/Sakshi-25/PostmanTesting/blob/main/ScreenShots/POSTMAN.jpg" width="50%"></img><img src="https://miro.medium.com/max/1200/1*tO_SemO2SWDsmN1bzIwmcA.png" width="50%" alt="https://miro.medium.com/max/1200/1*tO_SemO2SWDsmN1bzIwmcA.png" hover="https://miro.medium.com/max/1200/1*tO_SemO2SWDsmN1bzIwmcA.png"></img>


### Newman

Newman is an npm(Node Package Manager) technology that allows us to run and test Postman collections directly from the command line rather than Collection Runner. Npm is a package management system developed for the javascript programming language and accepted as a standard by Node.js. It can be run from the Npm command line. Thus, CI (Continuous Integration) can be easily installed on systems and servers (CircleCI, Jenkins, Travis CI, Gitlab, Bamboo). At this place, Newman can be imagined as a gateway to other tools.


### Newman integration

1. In order to run Postman Collections with Newman from the command line, you must first download and install node.js on your machine. Download and install node.js from https://nodejs.org/en/.

    After the installation has been completed, you can verify your npm version by typing the following command in the terminal.

     node -v

2. After installing Node.js, open the terminal. Install Newman with the following command below.

    npm install –g newman

    After the installation has been completed, you can check the version by typing the following command in the terminal.

    newman -v

3. Finally, you are ready to run your tests via the command line. This run activity can be performed in 2 different ways.

    Export the collection which you will run and go to the directory where that file is located from the command line. Then you can test the collection by running the following command.

    ***newman run ‘collection_name.json’***

    You can also run the tests via the link generated for collection. In fact, this method is much more effortless than exporting. Because each change made in the collection will be automatically affected on the collection link. You won’t have to spend any extra effort for the changes. However, doing this by exporting will cost us to get a new export for each change.

    ***newman run collection_link***

    NB

    -n : It is the feature that we define how many times we will run the collection. For instance, in order to run 10 times;

    ***newman run collection_name.json –n 10***

    -e : It allows us to use the variables used in the collection and defined in the environment file as in the Collection Runner. For instance;

    ***newman run collection_name.json –e environment.json***

    -g : Allows us to use the variables used in the collection and defined in the global file. For instance;

    ***newman run collection_name.json –g MyWorkspace.postman_globals.json***

### HTML Reporter

Newman also allows us to report the tests we run from the command line in HTML format. HTML reporter is quite convenient especially using CI server. This reporter comes with a dashboard style summary landing page and a set of different tabs which contain the detailed request information. It creates a much more detailed report than the console. It provides us to capture the body, header, params etc fields in detail for request and response. It helps us to debug failed tests and makes it easy for whole stakeholders in the project in order to review the test results with an overview.

You can complete HTML reporter installations by running the following instruction from the command line.

***npm install –g newman-reporter-htmlextra***

While running a collection, use the -r cli, htmlextra as in the command below. After the test is run, the HTML file will be automatically generated under the Newman folder in the related directory.

Install newman & htmlextra from the node.js command prompt using below commands:

npm install -g newman

npm install -g newman-reporter-htmlextra

After successful installation, run the below command

***newman run ""Reqres.postman_collection.json" --reporters=cli,htmlextra***


## Install Newman in Jenkins

Install Jenkins if you haven't already, and start it. By default, Jenkins is configured at http://localhost:8080 if you're running it locally. Install the NodeJS plugin in Jenkins, then install Newman in it.

### To install NodeJS in Jenkins, do the following:

1. Select Manage Jenkins.
2. Under System Configuration, select       Plugins.
3. Select Available plugins, and search for "NodeJS".
4. Select the checkbox next to NodeJS, and select Install.

To install Newman in Jenkins, do the following:

1. Select Manage Jenkins.
2. Under System Configuration, select Tools.
3. Under NodeJS installations, select Add NodeJS.
4. Enter a name for the NodeJS installation.
5. In Global npm packages to install, enter newman.
6. Select Save.

Configure Jenkins

After you install Newman in Jenkins, you can configure Jenkins to run a collection using Newman. You'll need a Postman Collection that has at least one request with tests. Then export the collection as a JSON file so you can run it using Newman.

Optionally, you can import a sample "Hello World" collection into your workspace to follow these instructions. Select the following Run in Postman button to import the collection.


To configure Jenkins to run Newman, do the following:

1. On the Dashboard page, select + New Item to create a new job.

2. Select Freestyle project from the options, name your project, and select OK.

3. On the Configure page, select Build Environment, and select the checkbox next to Provide Node & npm bin/ folder to PATH. Select the NodeJS installation where you installed Newman.

4. Select Build Steps, and select Add build step > Execute shell to run a shell command. Enter a shell command to run the collection using Newman.

Test Newman in Jenkins

1. On the Dashboard page, select the job you configured to run Newman.

2. Select Build Now to manually run the build. After the build runs, review the Build History to check if the build succeeded:

        If the build succeeded, Jenkins indicates this with a green checkmark.

        If the build failed, Jenkins indicates this with a red cross mark.

3. Select the build from the Build History, then select Console Output to review the results of the collection run.

4. If the build failed, go to the collection in Postman to fix your tests. Then export the collection as a JSON file, and run the build again.


