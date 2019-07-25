# Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets

We are using here NCD's Temperature and Humidity sensor, but the steps stay the equal for any of the **ncd** product, so if you have other ncd wireless sensors, experience free to observe alongside besides. By means of the stop of this text, you need to have a stable understanding of how to set up the sensors, configure node-red, and see the data on a dashboard like the one pictured right here.

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/Wireless%20Temp%20and%20Hum%20Sensor.png)
# IoT Long Range Wireless Temperature and Humidity  Sensor
Introducing NCD’s long-range wireless temperature humidity sensor, boasting up to a 28 Mile range using a wireless mesh networking architecture.  Incorporating the Honeywell HIH9130 temperature humidity sensor, transmits highly accurate temperature and humidity samples at user-defined intervals.

The on-board temperature sensor is rated for -25°C to 85°C or -13°F to 185°F and the humidity sensor is rated for 0 to 100% RH. It can be powered by just 2 AA batteries and an operational lifetime of 500,000 wireless transmissions.Battery life can be extended upto 10 years depending on environmental conditions and the data transmission interval.  Optionally, this sensor may be externally powered.

With an open communication protocol this IoT wireless temperature humidity product can be integrated with just about any control system or gateway.  Data can be transmitted to a PC, a Raspberry Pi, to Microsoft Azure® IoT, or Arduino. Sensor parameters and wireless transmission settings can be changed on the go using the open communication protocol providing maximum configurability depending on the intended application.

The long range, price, accuracy, battery life and security features of Long Range Wireless Temperature Humidity Sensor makes it an affordable choice which exceeds the requirements for most of the industrial as well as consumer market applications.

# Long Range Wireless Mesh Modem with USB Interface
![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/Zigmo.png)

# Resources Required
- [IoT Long Range Wireless Temperature Humidity Sensor](https://store.ncd.io/product/industrial-long-range-wireless-temperature-humidity-sensor/) with power source Battery Or External DC.
- [Zigmo/Router for PC](https://store.ncd.io/product/900hp-s3b-long-range-wireless-mesh-modem-with-usb-interface/)
- PC/Laptop with an OS installed or Any IoT Embedded Device.

# Setting up Node-Red.
The sensor and Zigmo/Router come pre-programmed and work out of the box. In this section we will setup a sensor and Zigmo link and start receiving data on our PC
# Steps to install NODE-RED
Now that you have sensors running, we need a way to do something useful with that data.
- First of all you'll have to install [Node-RED](https://nodered.org/docs/getting-started/installation). 
- Once that’s done, you’ll need to enter your command line, or Power Shell for Windows users, navigate to the directory Node-RED is installed in.
- Now type **“npm i ncd-red-wireless node-red-dashboard“**. This will install the nodes required to receive data from your wireless sensors and you can start Node-RED once this is done.
- To start node server write **node-red** in the command prompt or terminal and press enter.

# Setting up the nodes
Assuming at this point you’ve started up Node-RED, you should be able to open a browser and navigate to http://localhost:1880, this will open up the flow builder that is the heart of the Node-RED experience.

**Steps to build the flow**

- **At this point you’ll be viewing a large blank flow with a long list of nodes on the left hand side, this sidebar is called the palette.**

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/blankpage.JPG)

- **Go ahead and drag a Wireless Gateway node over to your flow canvas to get started.**

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/gateway%20step1.JPG)

- **ncd-red-wireless**
Provides the nodes that manage the serial connection, parse incoming sensor data, filter it by specific parameters, and allow you to configure the wireless sensors.

# Finding your wireless sensors
Once you’ve added the node you’ll be able to view the info tab, which contains information about the node’s functionality, this tab is well populated for most node-red packages and contains valuable information, many times you will not need to view any other documentation outside of the info tab, so keep it in mind while you are building your flows if you have a question about how a node works. The next thing we need to do is configure the node, when you first add it you’ll notice that there is a small triangle on the top right corner next to a blue dot, the triangle indicates that the node needs additional configuration, the blue dot indicates that the node has not yet been deployed as part of the flow.

- **Double click on the node to open up the configuration options.**

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/gateway%20step2.JPG)

- **Click on the pencil icon next to the Serial Device field to configure your USB router, this will open a second configuration panel that only has a few options.**

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/gateway%20step3.JPG)

- **Click on the magnifying glass next to the Serial Port field and select the port that corresponds with your router, then click the “Add” button on top. The Serial Device field will now be populated based on that selection, and you can click “Done”, you now have direct access to your wireless sensors! To view the data coming in.**

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/gateway%20step4.JPG)

- **Now go back to your palette and type “debug” into the search field at the top, grab one of these nodes and drag it to the right of your Wireless Gateway.**

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/debug%20step1.JPG)

- **Double click on it and change “msg.” to “complete msg object” click done.**

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/debug%20step2.JPG)

- **Now draw a line between the two nodes, and click “Deploy” on the top right of the window..**

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/deploy.JPG)

# Working with the data
Now out of your wireless sensors data is gathered and it is output to the “debug” tab, this "debug tab" is placed within the right sidebar subsequent to the information tab. To see the information are available in to hit the reset button. In node-red records is surpassed among nodes in a json packet. When the msg object comes into the debug tab you may make bigger it to view the overall list of information that comes with it. This is extraordinarily useful in case you need to quickly see which sensors are checking in. The other issue this node gives is a easy way to interchange your router to the network identity that devices in configuration mode document on, simply hit the button on the left of the node and the tool will switch to the configuration network, hit it once more to return it to listening mode. Once we get the wi-fi tool nodes set up, they may be set to routinely configure a sensor whilst it enters configuration mode, so it’s always available to maintain such a gateway nodes present at the flow for speedy configuring a device.

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/GatewayJson.png)

# Adding the wireless sensors
we need to separate wireless sensor records domestically in order that we are able to display it, we could use a switch node to split out the messages from the gateway based totally on the mac address with or sensor type, but as i referred to, the wireless nodes truly incorporate extra functionality for configuring the sensors, so we’ll start with them to give you a extra entire image of how those structures can work. In case you haven’t already seen packets coming in from both of your sensors, cross in advance and hit the reset button on the only that hasn’t stated. While a sensor assessments in thru any serial device configuration node, the mac address and kind of sensor is cached in a pool so we are able to quick find it for the duration of this next step.

- **Grab a Wireless Node from the palette and drag it onto the flow, double click on it to get it configured.**

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/wirelessdevice%20step1.JPG)

- **Select the serial device from the drop down that you used for the Wireless Gateway, now click the magnifying glass next to “Mac Address” and select one of the available options.**

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/wirelessdevice%20step2.JPG)

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/wirelessdevice%20step3.JPG)

You’ll notice this automatically sets the sensor type for you, you can also give it a name to make it easier to identify. As noted in the info tab, the Serial Device for Config field is optional, and we won’t worry about it right now. The node you have just added effectively works as a filter on incoming sensor data, only passing through data for the mac address, or sensor type if no mac address is present.

- **Now go back to your palette and type “debug” into the search field at the top, grab one of these nodes and drag it to the right of your Wireless Gateway.**

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/debug_wirelessdevice_step1.JPG)

- **Double click on it and click done.**

![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/debug_wirelessdevice_step2.JPG)

# Adding Function Nodes
The function node is used to run JavaScript code against the msg object. The function node accepts a msg object as input and can return 0 or more message objects as output. This message object must have a payload property (msg.payload), and usually has other properties depending on the proceeding nodes.

- **Now grab a “function” node from the palette, and place it to the right of the Temp/Hum node.**

 ![alt tag](https://github.com/rjrajbir/Creating-Email-Alerts-With-Node-Red-Of-NCD-Wireless-Temperature-and-Humidity-sensor/blob/master/temperature_function_node_step1.JPG)

- **Double click on the node to open up the configuration options.**

Here you have to write little javacript code to create a condition,so the temperature and humidity values will be written in the excel. 

 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/function_step2.JPG)
 
 - **Now Add "http request" node from the palette.**
 
 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/http_node_step1.JPG)
 
 - **If you double click on it edit http node,you'll see a "URL" field, here you have to enter the respective link of the googlesheet.**
 - **Now create googlesheet to store the values of temperature and humidity.**
 
 # Steps to create googlesheet.
 
 - **First open up your browser and type www.google.com and sign up in google account if you haven't signed in,then click on the six dots on  the left of your picture.**
 
 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step1.JPG)
 
 - **Now click on "Drive" to open the google drive.**
 
 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step2.JPG)
 
 - **Click on New>More>Google Forms>Blank Form.**
 
  ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step3.JPG)
  
  - **Here you'll see a untitled form,Give it some title as shown in the picture.**
  
  ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step4.JPG)
  
  - **Now edit question as Temperature and click on the "+" button to add another question for humidity.**
  
   ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step5.JPG)
   
   ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step6.JPG)
   
  - **Enter question as Humidity to take humidity values.**
  
  ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step7.JPG)
  
 - **Now click on the Three dots beside your picture as shown in the picture below.**
 
 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step8.JPG)
 
 - **Now click on the "Get pre-filled link".**
 
 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step9.JPG)
 
 - **Now enter random values to temperature and humidity fields and click Get link.**
 
 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step10.JPG)
 
 
 - **Now paste that link in notepad.**
 
  ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_notepad_step11.JPG)
  
 - **Edit that link as shown in the picture below.**
 
 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_notepad_step12.JPG)
 
 - **Now go back to form and click on RESPONSES and then click on the googlesheet icon as shown in the picture below.**
 
 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step14.JPG)
 
 - **Create a new spreadsheet.**
 
 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step15.JPG)
 
 - **Here you are able to see a new spreadsheet,then give it some name as shown in the pictures below.**
 
 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step16.JPG)
 
 - **Here you can visualize the values of temperature and humidity.**
 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/googlesheet_step17.JPG)
 
 - **Now go back to node-red and double click on http request node to edit it, then copy the URL from the notepad that you have saved and paste it in the URL field as shown in the figure.**
 
 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/http_node_step2.JPG)
You can also attach debug node to check the output the http node.

- **Now Connect all the wires.**

 ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/final_wire_connection.JPG)
 
 - **Click on Deploy button to get the out on the googlesheet.**
 
  ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/final_flow.JPG)
  
  # OUTPUT
  Now to go google spreadsheet and you'll see values are coming.
  
  ![alt tag](https://github.com/rjrajbir/Sending-data-of-wireless-Temperature-and-Humidity-Sensor-to-Googlesheets/blob/master/output.JPG)
