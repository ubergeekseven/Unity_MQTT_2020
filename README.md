# MichaelDot forked this to do this stuff....
I have forked the original repository with the changes outlined below. They forked it from the mentioned below as well. Unity no longer allows you to generate the object with "new". I instead created a public gameobject that would have the script on it. Then you would drag the gameobject into the editor spot so that the script can access the scritps on the gameobject. All scripts are on the same object so far but, this would allow you to also add the scripts to different objects and then reference them on an object that never disables and allows you to have all of your scritps in one location referencing objects as needed.

# Plans for this in the near future
I am working to add several capabilties to access quickly in unity.

multiple subscriptions with booleans or variables to pass strings
actions based off of received messages 2A) Allowing a phone or tablet to be an interface for the game. Currently working on projection mapping with multiple scenes. If I can pass a string along to a variable then, I could enter a new location on the network to look for videos to play in the virtual projection screen scene. Send a string that switches to the scene mentioned Booleans to trigger actions Buttons in an html page on a remote device could switch scenes, restart scenes or perform other tasks.
send updates for clients to read and print out 3A) Once a string is sent, then the game could acknowledge the receipt by sending back the string to hold in a seperate variable on the html page for displaying the updated information sent to the server. Button pushes could be verified server side and updated information sent back to show this visually
I will add scenes and examples as I improve on this library. So far I can receive info and do whatever with whtat comes in. Need to create editor scripts that are mor einformative and not require any coding on the original scripts after the fact. All from within the editor.


# Unity_MQTT
This is an edited version of [Unity3d_MQTT](https://github.com/vovacooper/Unity3d_MQTT) by vovacooper.  
  
I have made the variables more accessable to the user along with adding a routing script to keep the routing seperate from the main MQTT scripts.

## Usage

To use this script, first set the Client Settings 'Ip Address' to the address of your MQTT broker. The brokers port should be put in Broker_port feild. Ensure that a MQTT broker such as Mosquitto is running otherwise you'll get errors upon runtime. Ensure that you ensure the correct topics that you wish to subscribe too. 
All messages are routed throught the MQTT Routing script. Use this to cleanly breakdown the MQTT Topics and then prase the topic messages into usable data which you can then pass on to other functions or classes.

E.g.   

     if (MqttMessage.Topic.Contains("Global/Temperature")){     
     
          TemperatureControl TempCtrl = new TemperatureControl ();     
     
          int value = int.Parse(System.Text.Encoding.UTF8.GetString(MqttMessage.Message));   
     
          TempCtrl .setTemp(value );    
     
     }     

## Detail
  
![UI](ReadMe_Assets/MQTT_Image1.PNG "User Interface")

#### IP Address
IP of the broker.

#### Broker_Port
Port of the broker

#### Topic Prefix
Prefix that is added to all topics. E.g. in the example above, the topics subscriped to are: OC/TrackingPeople/IDs/#

#### Topics
This is a list of all the topics you wish to subscribe too. Use # as a wildcard

![MQTT](ReadMe_Assets/Capture7.PNG "MQTT Levels")
