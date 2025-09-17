ues.io comes with a database where you can configure your data schema for your Collections as explained in the [Collections](collections) documentation but you can also connect to other data sources and let ues.io extend the functionality that is missing from other platforms. You can connect to multiple data sources and view all of them in ues.io and work with their data.

There are connectors in the 'Bundle Store' which you can access from your 'Workspace' by clicking on the 'Installed Bundles' tile and then the 'Browse Bundle Store' button. We have Rest API and OData connectivity as a standard in our core so if you need a connection that is not in the 'Bundle Store' then you can simmply build your own with our 'Bots'.

The current connectors are available:

1. Salesforce
2. Smartsheet
3. ClickUp

## Salesforce

- Log into your Salesforce org and head over to the Setup cog and then to the App Manager menu.
- Click on the ‘New Connected App’ button (top right).
- Give your Connected App a Name and API Name, add your contact email.
- Select the ‘Enable Auth Settings’ checkbox and then you will see the settings menus.
- For the ‘Callback URL’ enter ‘https://studio.ues.io/site/oauth2/callback’
- For the ‘Selected OAuth Scopes’ choose ‘Access the identity URL service’ and ‘Access unique user identifiers’ and ‘Manage user data via APIs’ and ‘PErform requests at any time’.
- Check the ‘Require Proof Key for Code Exchange’ and ‘Require Secret for Web Server Flow’ and ‘Require Secret for Refresh Token Flow’ and ‘Enable Authorization Code and Credentials Flow’ and then ‘Save’.
- You will then see a view that tells you that it will take 10 minutes to take effect but it is normally quite quick.
- Select the ‘Continue’ button.
- In the next view select the ‘Manage Consumer Details’ button.
- Next you will see a view asking you to verify your identity by means of an email that was sent to the email address we entered when we created the connected app.
- Enter the code and ‘Verify’ and then you will see a view that displays the ‘Consumer Key’ and ‘Consumer Secret’ which we will use in the next steps.

## In ues.io

- Next head over to your ues.io app and to your Workspace and if you haven’t created an app yet you can read more about it in the [Create your first app](Create-your-first-app) documentation.
- Select the ‘Installed Bundles’ tile on the left and then select the ‘BROWSE BUNDLE STORE’ button. Look for the Salesforce Integration Bundle and install it.
- Then select the ‘Settings’ tile in your Workspace.
- Look under the ‘Secrets’ section and select the ‘uesio/salesforce.salesforce_client_id’ ‘SET’ button and then head back over to Salesforce and copy the ‘Consumer Key’ value and paste it in and select the ‘SET’ button and then Save.
- Then select the ‘uesio/salesforce.salesforce_client_isecret’ ‘SET’ button and then head back over to Salesforce and copy the ‘Consumer Secret’ value and paste it in and select the ‘SET’ button and then Save.
- Head back over to Salesforce to your connected app and copy the URL up to the end of ‘salesforce.com’. It should look like this: ‘https://'uesio2'-dev-ed.develop.my.salesforce.com/’.
- Then head back to the Workspace Settings and find the setting ‘uesio/salesforce.salesforce_url’ and then set the value with the URL you copied in the previous step.
- Go to the ‘Integrations’ section and deselect the ‘Only local integrations’ toggle and select the Salesforce integration and select the ‘TEST AUTHENTICATION’ button and ‘AUTHENTICATE’ to make sure your integration is authenticating. You should get a Salesforce popup asking you to enter the code that was emailed to you.
- Head over to the [Collections](collections) section in ues.io and create a new Collection.
- Name the new Collection ‘accounts’ and label ‘Accounts’ and label plural ‘Accounts’.
- Set the ‘Data Source Type’ to ‘External Integration’ .
- Set the ‘Data Source Integration’ to ‘Salesforce’ and set the ‘External Collection Name’ to Account, leave the rest blank and select ‘SAVE’.
- Create a new field for the Collection and enter ‘name’ for the name and ‘Label’ as ‘Accounts’, ‘Type’ as ‘Text’ and ‘External Field Name’ as ‘Name’.
- Then edit the collection and set the 'Name Field' to 'name' and Save.
- Now head over to the [Views](views) tile and then create a view called 'account' and then select the 'Build' button.
- Select the 'WIRES' option and select the '+ COLLECTION WIRE' then move up to the 'Collection' dropdown and select the 'accounts' collection.
- Select the 'FIELDS' option and the '+ COLLECTION FIELD' and select the 'name' field.
- Next head over to the components tile and place a table in the canvas.
- Move over to the Tables properties section (top left) and select the 'Wire' you created.
- Select the 'COLUMNS' option and click on '+ ADD COLUMN' then select the 'Field' tile and then the 'Field' dropdown and selct the 'name' field.
- You will see a list of all the Accounts in Salesforce.

## Connectors in Production - Site Deployment

We connected to Salesforce in the Studio [Workspace](workspaces) which will allow you to build out your app while you are connected to the Salesforce instance but to move to production and a Site you will need to have your users login to the Site and perform an authentication into Salesforce from there. To do that you will need:

- Create a login method.
- A custom login view.
- A view with the workflow to perform the Salesforce authentication.
- User Profile and associated permission set to auto assign to new and existing users.

## 2. Smartsheet

- Docs available on request

## 3. ClickUp

- Docs available on request

## 4. REST

- Docs available on request
