**Kore.ai**

**Chatbot Test Runner **

**Tool**

[[TOC]]

### Overview

Kore.ai Chatbot Test Runner enables you to substantially cut down your bot development team’s QA efforts by automating the creation, execution of test cases, and fast-track bug fixing by providing comprehensive test results and steps to reproduce. 

As with regular bot testing, the first step is to define different test scenarios and flows and interacting with the bot to check the responses. However, most of what follows next reduce the manual efforts to a large extent. 

The Chatbot Test Runner records these interactions and organizes them into test cases that included your entries as inputs and bot responses as the expected output. You can conduct any number of chat sessions to record separate test suites depending on your test strategy. You can download the recorded test suites for reuse and edit them to better suit your test expectations. The tool also allows you to download the Steps to Reproduce (STR) file for all your bot interactions. You can use these steps to reduce the redundancy of having to write the content all over again when you are reporting the bugs. 

Once you finalize the test suites, you can put them back into the Chatbot Test Runner to execute these test cases at various stages of your bot development, without investing enormous bandwidth in conducting the interactions all over again. 

Every time you run the test cases using the Chatbot Test Runner, it produces a Test Results spreadsheet for each test suite. The spreadsheet provides a comprehensive report of the test run, with the developer input, actual and expected results, and the status the test run as passed or failed. You can use this spreadsheet to report, keep a track of, and re-test the failed test cases.

### Prerequisites

* **Python 3.7: **The Chatbot Test Runner requires Python 3.7 or later version to run the automated test scripts. If you do not already have the software, download the suitable version for your operating system from here: [https://www.python.org/downloads/](https://www.python.org/downloads/)

* **Kore.ai Web SDK Configuration: **Kore.ai offers Bots SDKs as a set of platform-specific client libraries that provide a quick and convenient way to integrate Kore.ai Bots chat capability into custom applications. The Bots Web SDK contains HTML5 and JavaScript libraries that enable you to talk to Kore.ai bots over a web socket. You need to configure the Bots Web SDK to be able to use the Chatbot Test Runner on your bot applications. [Read how to configure Web SDK](#bookmark=id.r2ivhwkjsmln)

### Chatbot Test Runner **Configuration Steps**

Configuring Chatbot Test Runner involves the following major steps:

* **Step 1:** **Download the Chatbot Test Runner from GitHub: **The [Chatbot Test Runner repo](https://github.com/Koredotcom/chatbot-test-runner) contains the necessary libraries to configure, record and run the test cases over Web SDK. 

* **Step 2: Configure Kore.ai Web SDK**:  Setting up the Web SDK integration for your web application involves creating an app in the bot for authentication and enabling Web/Mobile Channel for the bot. You need to add the app and the bot details in the downloaded repo to create a communication channel between the application and bot. [Read how to configure Web SDK](#bookmark=id.r2ivhwkjsmln)

* **Step 3**: **Plan, Record, and Download Test Cases**: Define the various scenarios to test along with expected outcomes. Execute these interactions with the bot. The Chatbot Test Recorder records the entire interaction and organizes them as the test cases which you can download and edit later. Also, you can plan the interactions in a way that suits your testing strategy such as by task, sub-tasks, etc. For example, let’s consider you want to manage the test cases for each bot task separately. In that case, you can execute the interactions in such a way that they reflect the flows in the specific task. After completing the testing of scenarios in that task, you can end the conversation. The recorded Test Cases file now only includes the task-specific cases. Similarly, you can run more interactions for the other bot tasks and download the respective TestSuite files. 

* **Step 4: Auto-Run the Test Suites:** Once you record one or more Test Suites, you can execute them with little manual intervention anytime later. You need to upload the test suites to the Test Runner and specify the names of the Test Suites you want to run for before each follow-up execution. After each run, the tool creates Test Results spreadsheets to the Test Case files that you can use to track the results from the test run. 

* **Step 5: Track and Report the Results:** Use the Test Results spreadsheets to look into the** **failed test cases. The STR file that you can download after a test run can help you copy the steps to reproduce the bugs and reduces the task of writing the steps down manually to report them. 

### **Step 1**:** Download the ****Chatbot **Test Runner** from GitHub**

You can download the Chatbot Test Runner tool from our public repository at [https://github.com/Koredotcom/chatbot-test-runner](https://app.kore.com/https%3A%2F%2Fgithub.com%2FKoredotcom%2Fchatbot-test-runner)

The repo contains the following folders:

![image alt text](image_0.png)

The Test Recorder folder consists of the Index file in the following path: 

<table>
  <tr>
    <td>\chatbot-test-runner-master\TestRecorder\web-kore-sdk\UI\Index.html</td>
  </tr>
</table>


It is in this file that you set up the Web SDK configuration.

You need to edit the following files in the Chatbot Test Runner folder:

<table>
  <tr>
    <td>TestSuites (folder)</td>
    <td>Upload the test cases JSON files into this folder</td>
  </tr>
  <tr>
    <td>Test_Config</td>
    <td>Enter the host address, bearer token, and other configuration details in this file</td>
  </tr>
  <tr>
    <td>TestSuites(file)</td>
    <td>Enter the names of one or more of the uploaded test suites files that you would like to run. On running the tool, it only executes those test suites specified in this file.</td>
  </tr>
  <tr>
    <td>install_windows</td>
    <td>Run this batch file to execute the test cases in the specified test suite files. </td>
  </tr>
  <tr>
    <td>TestResults</td>
    <td>Includes the test result spreadsheets for each corresponding test suites you execute. </td>
  </tr>
</table>


### Step 2: Configure Kore.ai Web SDK

Follow these steps to configure Kore.ai Web SDK for your application:

1. Open the bot for which you want to configure the Web SDK.

2. If you haven’t already created a client app in the bot for authentication, go ahead and create one. Read [SDK App Registration](https://developer.kore.ai/docs/bots/kore-web-sdk/sdk-app-registration/) article to learn how to.

3. After you create the app, you need to enable Web/Mobile Client channel for the bot. To do so, on the bots main menu, click **Channels**. 

4. Under All Channels, click **Web/Mobile Client**. The channel setup window slides open.

5. From the **Select App** drop-down list, select the app you create. The Bot Name, Bot Id, Client ID, Client Secret details open. To copy the app registration details to the clipboard for your application, you can click Copy for Bot Name, Bot ID, and Client ID. For Client Secret, click View, and then click Copy.

6. Under the **Allow Alert task setup**, select **Yes, let the users setup alert tasks using the web client** to enable your application users to set up their own alert tasks using the web client. By default, this setting is disabled for web client users, but mobile client users can always setup their own alerts.

7. Under **Enable Channel**, select **Yes**. 

8. Click **Save **to save the settings and close the Web/Mobile Client Channel page.
The Channel Information updated successfully message is displayed near the top of the page.

After you enable the channel, you need to enter the relevant details in the index file in the Chatbot Test Runner tool that you download. The index.html file is available at *\chatbot-test-runner-master\TestRecorder\web-kore-sdk\UI\Index.html *in the downloaded repo.

Edit the file using Notepad++and enter the following details in the file:

<table>
  <tr>
    <td>botOptions.JWTUrl</td>
    <td>Enter the JWTURL that you admin has set up for you. This URL is specific to your organization. Contact your admin to set up or find out the URL.</td>
  </tr>
  <tr>
    <td>botOptions.userIdentity</td>
    <td>Enter the email address of a user on the bot. </td>
  </tr>
  <tr>
    <td>botOptions.botInfo</td>
    <td>Name: enter the name of the bot. Bot name is case sensitive.
Id: Enter the Bot ID. You can access it from the Web/Mobile Client Channel page or the General Settings page of the bot.</td>
  </tr>
  <tr>
    <td>botOptions.clientId</td>
    <td>Enter the Client ID of the app you are using for authentication. You can access it from the Web/Mobile Client Channel page.</td>
  </tr>
  <tr>
    <td>botOptions.clientSecret</td>
    <td>Enter the Client Secret of the app you are using for authentication. You can access it from the Web/Mobile Client Channel page.</td>
  </tr>
</table>


After you make these entries, on the Notepad++ menu, click Run > Launch in Chrome. If it opens a chat window with the name of the bot displayed on it over the browser, it means the configuration is successful. 

### Step 3: Record, Edit, and Download Test Cases

When you download the Chatbot Test Runner tool and configure Web SDK, the tool records your conversations with the bot in each session and organizes them as test cases. The input for the test case would be your entries and the bot responses those entries would be considered as expected output. 

Here’s a sample conversation to test ambiguous input for a List of Values Entity:

![image alt text](image_1.png)

The tool captures this conversation as the following test case in a nested JSON object:

<table>
  <tr>
    <td> "messages":[  
            {  
               "input":"Static list of values",
               "outputs":[  
                  {  
                     "contains":"Please select one of the values.\n\na) Mango Fruit\nb) Apple Fruit\nc) Test Grapes fruit\nd) Custom Packs\ne) 1 GB 2G For 28 Days 147 Rs\nf) 1 GB 3G For 28 Days 147 Rs\ng) 1 GB 3G For 28 Days @ 155 Rs.\nh) VSS\ni) Password\nj) Create An Incident\nk) Orange Fruit\nl) New Data Offers\n"
                  }
               ]
            },
            {  
               "input":"Fruit",
               "outputs":[  
                  {  
                     "contains":{  
                        "allOf":[  
                           "The value you entered seems to be ambiguous. Tell me the option you would like to choose. \n",
                           "Mango Fruit",
                           "Apple Fruit",
                           "Test Grapes fruit",
                           "Orange Fruit"
                        ]
                     }
                  }
               ]
            },
            {  
               "input":"Orange Fruit",
               "outputs":[  
                  {  
                     "contains":"{&quot;LOV&quot;:&quot;Orange Fruit&quot;}\n"
                  }
               ]
</td>
  </tr>
</table>


To denote the end of a test case, you need to enter discard all after the interaction related to the test case is completed. The tool closes the test case when it encounters discard all. It treats the interaction after discard all as a new test case. 

Take a look at the sample below for a sample:

![image alt text](image_2.png)

Here’s the downloaded test suite that starts a new test case (TC2) after the discard all:

<table>
  <tr>
    <td>{  
   "botName":"Bot Test Automation",
   "botId":"st-3644696f-72e6-5d35-a080-96afd1c2d865",
   "testCases":[  
      {  
         "discardBefore":true,
         "name":"TC1",
         "messages":[  
            {  
               "input":"Static list of values",
               "outputs":[  
                  {  
                     "contains":"Please select one of the values.\n\na) Mango Fruit\nb) Apple Fruit\nc) Test Grapes fruit\nd) Custom Packs\ne) 1 GB 2G For 28 Days 147 Rs\nf) 1 GB 3G For 28 Days 147 Rs\ng) 1 GB 3G For 28 Days @ 155 Rs.\nh) VSS\ni) Password\nj) Create An Incident\nk) Orange Fruit\nl) New Data Offers\n"
                  }
               ]
            },
            {  
               "input":"Fruit",
               "outputs":[  
                  {  
                     "contains":{  
                        "allOf":[  
                           "The value you entered seems to be ambiguous. Tell me the option you would like to choose. \n",
                           "Mango Fruit",
                           "Apple Fruit",
                           "Test Grapes fruit",
                           "Orange Fruit"
                        ]
                     }
                  }
               ]
            },
            {  
               "input":"Orange Fruit",
               "outputs":[  
                  {  
                     "contains":"{&quot;LOV&quot;:&quot;Orange Fruit&quot;}\n"
                  }
               ]
            }
         ]
      },
      {  
         "discardBefore":true,
         "name":"TC2",
         "messages":[  
            {  
               "input":"Convert Currency 100 USD to 100 INR",
               "outputs":[  
                  {  
                     "contains":" Code of Currency1 is INR\nAmount of Currency 1 is 100\nCode of Currency2 is USD\nAmount of Currency2 is 100\n"
                  }
               ]
            }
         ]
      }
   ]
}</td>
  </tr>
</table>


#### Commands for Test Case Recording

* As you are recording your bot interaction to create test cases, type** ****_discard all _**when you want the recorder to end a particular test case and start a new one. The discussion following discard all gets recorded as a new test case in the same Test Suite file. 

* To start a new Test Suite, refresh or restart the index page that 

#### Downloading the Recorded Files

* To download the recorded test suites click the Download Test Suite button on the top-left side of the test recorder window.

* To download the steps to reproduce for the interaction, click Download STR.

#### Planning the Test Suite Recording

The key here is that the tool in itself doesn’t interpret the validity of the bot responses. It just records every bot response with an assumption that is the valid response to the user input. The onus is on the testing team to ensure that the recorded test cases represent valid inputs and outputs. 

The following are some best practice you can use to plan and generate the test cases using the Chatbot Test Runner tool:

* **Manage your Recording Sessions Based on your Test Strategy**: Categorize the test cases so that you can conduct connected interactions with then bot in one session and manage the resultant test case file separately based on your test strategy. For example, you can think of all the test cases related to a particular task and execute those interactions with the bot. This allows you to download the test case file after the completion of the interaction and helps you manage the test cases of the task separately. 

Tip: For each group of test cases to be recorded, download the Test Case file by clicking **Download Test Suite **and close the chat window. It ends the session. When you start a new chat it opens a new session in which you can record another Test Suite. 

* **Test Run the Interactions before Final Execution**: The Chatbot Test Runner tool merely records your interactions with the bot and treats your entries as inputs and bot responses as expected output. It helps to record optimum test cases if you do a few dry runs before the interaction that is optimum to download. 

* **Review and Edit Each Test Suite:** After downloading a Test Suite file, get it reviewd to check the validity of the test cases. You can directly make any minor changes directly in the file. You would specifically need to edit the file in these cases:

    * **Multiple Possible Bot Responses:** Some inputs can have multiple possible bot responses such as standard responses. In these cases, the bot often picks one of the possibilities. However, the other options are equally valid and the Test Suite must include all the possibilities so that it doesn’t give a false negative for other bot responses. You can edit such cases as follows using oneOf:

<table>
  <tr>
    <td>            "outputs": [{
                "contains": " Color entered is &quot;red&quot;\n"
                    },
					{
				  "contains": {
                          "oneOf": [
                          "Should I continue with the task 'Person Name'?  ",
                          "Should we continue the previous task of 'Person Name'?  ",
                          "Do you want to pick up where we left off for 'Person Name'?  ",
						  "Would you like to continue with the task 'Person Name'?  "
                                ]}
				  }
                    ]</td>
  </tr>
</table>


### Step 4: Running the Test Suites

After you record and download the test suites, you can auto-run them using the Chatbot Test Runner tool any number of time as the bot development progresses. You can run multiple test suites in each run and add and remove the test suite to suit your requirements. 

#### Configuring the Test Runs:

Configure the following settings to execute the Chatbot Test Runner:

* **Upload the select TestSuite files**: In the TestSuites folder(*chatbot-test-runner-master\TestRunner\WebSocketAutomation\TestSuites*), upload the Test Suites  JSON files you want to run. You can upload one or more files to execute at once. Each test suite will result in a corresponding test results spreadsheet in the TestResults folder. 

* **Enter test configuration details**: In the test_config file (*chatbot-test-runner-master\TestRunner\WebSocketAutomation\test_config.json*) file make the following entries:

    * **Host: **Enter the URL of your Bot Builder instance, for example, https://bots.kore.ai

    * **AuthToken**: Enter the bearer token for bot authentication. Follow these steps to find the bearer token from the bot builder:

        1. Open the bot that you want to test in Google Chrome.

        2. Press F12 to open the developer console. 

        3. Click the Talk to Bot icon at the right-bottom of the bot window to open the chat.

        4. On the developer console of Chrome, click Network > XHR > Start. When you scroll down the details as shown in the following image, you can see the bearer token with authorization as the heading. Copy the code and exclude the word bearer. 
![image alt text](image_3.png)

    * **Builder**: Enter **true **if you want to test both configured and published tasks. To test only the published task, set this value to **false**. Setting it to false improves the performance as the tool only checks the published tasks. 

* **Enter the names of the test suites to execute in the current run**: In the TestSuite.JSON file *(\chatbot-test-runner-master\TestRunner\WebSocketAutomation\TestSuite.json*), enter the names of the test suite files to be executed in this run. These files should be uploaded in the TestSuite folder to get executed. Enter the name as follows:

<table>
  <tr>
    <td>{
    "testCases":[
        "TestSuite1",
        "TestSuite2"
    ]
}
</td>
  </tr>
</table>


* **Execute the Test Run**: Double-click the** ****install_window** batch file. Once the file completes initialization, type the following command:

<table>
  <tr>
    <td>python test.py</td>
  </tr>
</table>


After running successfully, the Chatbot Test Runner executes all the test cases and records in the results in the TestResults folder. 

### Step 5: Track and Report the Results

After every successful execution of the Chatbot Test Runner, it records the results in the TestResults folder. The folder consists of spreadsheets one each for the test suites that the tool executed. The following is a sample test results spreadsheet:
![image alt text](image_4.png)

You can check for the failed test cases from the Result section. You can also use the STR download file for content to raise bugs. 

