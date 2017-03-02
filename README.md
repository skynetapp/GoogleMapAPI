#### Date: 02-03-2017
#### Description: This module points the multiple jobs address on map based on the city search.

#### The Folder Structure is as follows:

 Root Directory | Sub Directory 
------------ | -------------
index.php | 
Global | DBMySQL, XMLGenerator
Lib | Smarty
Modules | GoogleAPIController, GoogleAPIDataAction, GoogleAPIMysql, GoogleAPIView
Views | getMap.tpl
js | locationJS.js


#### Step 1:

Based on the url, map will be loaded with a textbox to enter city and search the jobs on it.

#### Step 2:

When user enters the city name and submits, it will call the module **googleMapAPI** and corresponding action **GetList** from index.php

#### Step 3:

In action **GetList** from index.php, Function **getJobsDataFromMySQL** will be called from index.php to controller.

- Function **getAllJobsAddressDataFromMySQL** will be called in controller to action and set the DBMYSQL connection by calling function **setGoogleAPIMySQLConnection**.
- Function **getJobsAddressDataFromMySQL** will be called from action to Mysql which will execute the query to get the jobs address based on the city and returns the result.
- The result set will be passed to function **generateXMLWithResultSet** in controller to action. The result set will be executed one by one and will generate the marker location based on the address, latitude and longitude.
- Function **generateMarkerLocation** will get the parameters and generate the marker location and will return the xml.

#### Step 4:

- The Generated xml data and the mysql result set will be passed to function **showJobsAddressListView** in controller to view.
- In view, we will parse the generated xml and the resultset will be passed to display the address in tpl page.

#### Step 5:

- When we click on the output address, based on latitude and longitude , we can point to that address in map.
- Here script will get the latitude and longitude and show the marker on the map.
