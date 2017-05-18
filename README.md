# PhonePi_SampleServer
This is a simple Flask based server with WebSocket support that accepts the sensor data and writes it to a text file. This is a companion sample server fo the PhonePi Sensor Streamer app.

# Steps:
* Clone the repository or download the zip file and unzip it to a directory of your choice.
* cd to the directory where the folder was extracted

## To Run the Server (Python 2.7)
```
 source PhonePi_SampleServer-master/bin/activate
 cd PhonePi_SampleServer-master
 pip install -r requirements.txt
 python PhonePi.py 

```
You can make any changes you want to to PhonePi.py

## Data Format Cheat sheet:
* Accelerometer: x,y,z
* Gyroscope: x,y,z
* Magnetometer: x,y,z
* Orientation: azimuth,pitch,roll
* Step Counter: steps
* Thermometer: temperature
* Light Sensor: light
* Proximity: isNear, value, maxRange
* Link: https://github.com/kprimice/react-native-sensor-manager

# Server details
This makes use of flask_sockets. Note the use of namespaces which are in accordance with the sensor's name. Sample code:

```python
@sockets.route('/accelerometer') 
def echo_socket(ws):
	 f=open("accelerometer.txt","a")
	 while True:
		message = ws.receive()
		print(message) 
        	ws.send(message)
		print>>f,message
	 f.close()
```
The app would then establish a connection to ws://url//accelerometer
where url is what the user enters (ip address:port) 


