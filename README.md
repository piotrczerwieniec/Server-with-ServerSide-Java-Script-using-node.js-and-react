# step by step
1. Open a terminal window by using the menu in the editor: Terminal > New Terminal.
verify that node CLI is installed.
node --version
You should see output similar to this, though the versions may be different:

v12.18.3
Change to your project folder.
cd /home/project
Clone the git repository that contains the artifacts needed for this lab, if it doesn't already exist.
git clone https://github.com/ibm-developer-skills-network/lkpho-Cloud-applications-with-Node.js-and-React.git
Change to the directory for this lab.
cd lkpho-Cloud-applications-with-Node.js-and-React/CD220Labs/http_server
List the contents of this directory to see the artifacts for this lab.
ls
Check the content of index.js. This is the server side script we will run in the next section.
cat index.js
You should see output similar to this.

const http = require('http');

const requestListener = function (req, res) {
  res.writeHead(200);
  res.end('Hello, World!');
}

const port = 8080;
const server = http.createServer(requestListener);
console.log('server listening on port: ' + port);
Alternatively, you can also view the content of index.js through the file explorer menu. It would appear like this.


Step 2: Use the node CLI
In order to start the server, we run the index.js file with the node command.
node index.js
You should see output similar to this.

server listening on port: 8080
To split the terminal, click Terminal > Split Terminal.

In the second terminal window, use the curl command to ping the application.
curl localhost:8080
You should see output similar to this.

Hello, World!
It should indicate that your app is up and running.

To verify the same with browser window, click on Launch Application in the menu.

A window will pop up as below for you to enter the port number. Enter the port number the server is running on, which is 8080 in it.


A new browser window will open up as below. (Note: New browser window may not open up if you browser settings does not allow pop-ups)


To stop the server, go to the main command window and press Ctrl+c to stop the server and stay in that terminal.
Step 3: Use the node CLI to run server script which requires another module
In the same terminal, check the content of today.js.
cat today.js
You should see output similar to this.

module.exports.getDate = function getDate() {
    var aestTime = new Date().toLocaleString("en-US", {timeZone: "Australia/Brisbane"});
    return aestTime;
}
Alternatively, you can also view the content of today.js through the file explorer menu. It would appear like this.


We will use this exported module in the server side script.

Check the content of index-with-require.js. As you will observe, this script requires the module today whose content we saw in the previous step.
cat index-with-require.js
You should see output similar to this.

const http = require('http');
const today = require('./today');

const requestListener = function (req, res) {
  res.writeHead(200);
  res.end(`Hello, World! The date today is ${today.getDate()}`);
}

const port = 8080;
const server = http.createServer(requestListener);
console.log('server listening on port: ' + port);
Alternatively, you can also view the content of index-with-require.js through the file explorer menu. It would appear like this.


In order to start the server, we run the index-with-require.js file with the node command.
node index-with-require.js
You should see output similar to this.

server listening on port: 8080
In the second terminal window which you opened earlier, use the curl command to ping the application.
curl localhost:8080
You should see output similar to this.

Hello, World! The date today is Wed Oct 14 2020 14:56:42 GMT+1030 (Australian Eastern Standard Time)
It should indicate that your app is up and running.

To verify the same with browser window, click on Launch Application in the menu.
Enter the port number 8080 in the window which pops up.

A new browser window will open up which show Hello World! along with the date and time in your time zone.
