# ESP8266

## Contents

1. [Introduction to IoT and ESP8266](https://github.com/poseidon078/eclub-iitk-esp8266#introduction)

2. [Project](https://github.com/poseidon078/eclub-iitk-esp8266#project)

3. [Controlling an LED through the Internet - ](https://github.com/poseidon078/eclub-iitk-esp8266#project-one-controlling-an-led-through-the-internet)
- [Hardware and software required](https://github.com/poseidon078/eclub-iitk-esp8266#hardware-and-software-required)
- [Working](https://github.com/poseidon078/eclub-iitk-esp8266#working)
- [Installing ESP8266 platform](https://github.com/poseidon078/eclub-iitk-esp8266#installing-the-esp8266-platform)
- [Uploading the Code](https://github.com/poseidon078/eclub-iitk-esp8266#connections-and-uploading-of-the-code)
- [Execution](https://github.com/poseidon078/eclub-iitk-esp8266#running-disconnection-and-powering)

4. [Receiving MPU6050 data over the Internet - ](https://github.com/poseidon078/eclub-iitk-esp8266#project-two-receiving-mpu6050-data-over-the-internet)
- [Hardware and software required](https://github.com/poseidon078/eclub-iitk-esp8266#hardware-and-software-required-1)
- [Working](https://github.com/poseidon078/eclub-iitk-esp8266#working-1)
- [Uploading Bare Minimum](https://github.com/poseidon078/eclub-iitk-esp8266#uploading-the-bare-minimum-code)
- [Uploading main code](https://github.com/poseidon078/eclub-iitk-esp8266#connections-and-uploading-of-the-main-code)
- [Connecting MPU6050 to UNO](https://github.com/poseidon078/eclub-iitk-esp8266#making-of-mpu6050-esp8266-uno-joint-connection)
- [Execution](https://github.com/poseidon078/eclub-iitk-esp8266#execution)
- [Switch to Internet](https://github.com/poseidon078/eclub-iitk-esp8266#switch-to-internet-and-powering)

5. [Interesting Readings](https://github.com/poseidon078/eclub-iitk-esp8266#external-references-that-may-be-read)

6. [References used](https://github.com/poseidon078/eclub-iitk-esp8266#bibliography)

## Introduction
Ever wanted to control another device from a distance? Ever fathomed making a joystick of your own? Or felt bored of using the keyboard for playing games? Here's how ESP8266 and IoT shall come to your rescue and make your friends feel jealous of you.

So what is ESP?

Nothing but an acronym for Espressif, Inc. That firm is credited with the making of ESP8266, a **low-cost Wi-Fi microchip, with a full TCP/IP stack and microcontroller capability**. Hey, some big terms were stated there, which are related to the Internet! So lets clear our understanding of Internet-or rather the Internet of Things and relate it to our ESP8266.

**The Internet** is the global system of interconnected computer networks that uses the Internet protocol suite (TCP/IP) to communicate between networks and devices. The Internet protocol suite is the conceptual model and set of communications protocols used in the Internet and similar computer networks. It is commonly known as TCP/IP because the foundational protocols in the suite are the Transmission Control Protocol (TCP) and the Internet Protocol (IP). In telecommunication, a communication protocol is a system of rules that allow two or more entities of a communications system to transmit information via any kind of variation of a physical quantity. Protocols may be implemented by hardware, software, or a combination of both.

Communication over the internet happens through 'packets' of data. The
**Internet Protocol (IP)** has the task of delivering packets from the source host to the destination host solely based on the IP addresses in the packet headers. For this purpose, IP defines packet structures that encapsulate the data to be delivered. It also defines addressing methods that are used to label the datagram (the unit of transfer in this 'packet' system) with source and destination information. **The Transmission Control Protocol (TCP)** provides reliable, ordered, and error-checked delivery of a stream of octets (bytes) between applications running on hosts communicating via an IP network.

**Wi-Fi** is a family of wireless networking technologies, which are commonly used for local area networking of devices and Internet access. **Access point (AP)** is a networking hardware device that allows other Wi-Fi devices to connect to a wired network. An AP connects directly to a wired local area network and the AP then provides wireless connections using wireless LAN technology, typically Wi-Fi, for other devices to use that wired connection. It has a unique IP address which can be used/accessed by anyone on the network to communicate with someone else on that network.

Recall the way we defined ESP8266: a low-cost Wi-Fi microchip, with a full TCP/IP stack and microcontroller capability. So it is a device with embedded wireless networking technology on which the communication protocols (TCP/IP) are established and can be used to control other devices-an LED bulb for instance.

![ESP8266-01](/p.jpg)

Moreover, the ESP8266 module has three operational modes:

1. Access Point (AP) — In AP, the Wi-Fi module acts as a Wi-Fi network, or access point (hence the name). It allows other devices to connect to it. And establishes a two-way communication between the ESP8266 and the device that is connected to it via Wi-Fi.

2. Station (STA) — In STA mode, the ESP-01 can connect to an AP (access point) such as the Wi-Fi network from your house. This allows any device connected to that network to communicate with the module.

3. Both — In this mode ESP-01 acts as both an AP as well as in STA mode.

You can switch these modes using **AT commands**: instructions used to control a modem. A Modem is a hardware device that converts data into a format suitable for a transmission medium so that it can be transmitted from one computer to another. Here our modem is the ESP8266.

## Project

I'll guide you to the completion of two very interesting projects in which the ESP8266 works in the STA mode:

- **Controlling an LED through the Internet.** (Receiver: ESP8266)
- **Receiving MPU6050 data over the Internet.** (Transmitter: ESP8266)

### Project One: Controlling an LED through the Internet

#### Hardware and Software required
- ESP8266-01 board
- Arduino UNO board
- Jumper wires
- LM1117
- LED bulb
- 3.3v power source
- Internet connection
- Arduino IDE
- ESP8266 Arduino IDE library(Guide to installation given later)
- Two 4 pin push buttons

#### Working
The ESP-01 module has GPIO pins which can be programmed to turn an LED ON/OFF through the internet. The module can be programmed using Arduino UNO through the serial pins (RX,TX). The general structure of the plan is: making the circuit connecting UNO-ESP8266-LED, then uploading the code onto it, establish the wireless connection between the circuit and the computer, disconnect the ESP8266 and connect it to a power source and then finally play with the LED. See the image for a flowchart representation of our project:

![flowchart](/flow.jpg)

#### Installing the ESP8266 platform:
First, the Arduino environment has to be set up to make it compatible with the ESP-01 module. It is required to have Arduino version 1.6.4 or higher in order to install the ESP8266’s platform packages.

1. Open the preferences window from the Arduino IDE. Go to File >Preferences

![flowchart](/install1.png)

2. Enter http://arduino.esp8266.com/stable/package_esp8266com_index.json into Additional Board Manager URLs field and click the “OK” button

![flowchart](/install2.png)

3. Open boards manager. Go to: Tools > Board > Boards Manager…

![flowchart](/install3.png)

4. Scroll down, select the ESP8266 board menu and install “esp8266 platform”.

![flowchart](/install41.png)

5. Choose your ESP8266 board from Tools > Board > Generic ESP8266 Module

![flowchart](/install4.png)

#### Connections and Uploading of the Code
You can now use the Arduino UNO to flash the code to ESP8266 ESP-01, but then we have to use manual flashing. For this, we use two push buttons. Refer to the following diagram:

![flowchart](/working2.jpg)

While uploading the code, follow the procedure to keep the flash button pressed while you click once on reset and release the flash button.

Connections (ARDUINO ---------------> ESP8266) :
- GND---------------------->GND
- TX------------------------>TX
- RX------------------------>RX
- Reset Button------------>RST
- Flash Button------------>GPIO0

Select your ESP8266 board from Tools -> Board -> Generic ESP8266 Module. Now copy the code given here to the Arduino IDE. Press the upload button. Now change SSID into your Wi-Fi access point and the password to your Wi-Fi password and compile.

```
#include <ESP8266WiFi.h>

const char* ssid = "YOUR_SSID";//type your ssid
const char* password = "YOUR_PASSWORD";//type your password

int ledPin = 2; // GPIO2 of ESP8266
WiFiServer server(80);//Service Port

void setup() {
Serial.begin(115200);
delay(10);

pinMode(ledPin, OUTPUT);
digitalWrite(ledPin, LOW);

// Connect to WiFi network
Serial.println();
Serial.println();
Serial.print("Connecting to ");
Serial.println(ssid);

WiFi.begin(ssid, password);

while (WiFi.status() != WL_CONNECTED) {
delay(500);
Serial.print(".");
}
Serial.println("");
Serial.println("WiFi connected");

// Start the server
server.begin();
Serial.println("Server started");

// Print the IP address
Serial.print("Use this URL to connect: ");
Serial.print("http://");
Serial.print(WiFi.localIP());
Serial.println("/");
}

void loop() {
// Check if a client has connected
WiFiClient client = server.available();
if (!client) {
return;
}

// Wait until the client sends some data
Serial.println("new client");
while(!client.available()){
delay(1);
}

// Read the first line of the request
String request = client.readStringUntil('\r');
Serial.println(request);
client.flush();

// Match the request

int value = LOW;
if (request.indexOf("/LED=ON") != -1) {
digitalWrite(ledPin, HIGH);
value = HIGH;
} 
if (request.indexOf("/LED=OFF") != -1){
digitalWrite(ledPin, LOW);
value = LOW;
}

//Set ledPin according to the request
//digitalWrite(ledPin, value);

// Return the response
client.println("HTTP/1.1 200 OK");
client.println("Content-Type: text/html");
client.println(""); //  do not forget this one
client.println("<!DOCTYPE HTML>");
client.println("<html>");

client.print("Led pin is now: ");

if(value == HIGH) {
client.print("On");  
} else {
client.print("Off");
}
client.println("<br><br>");
client.println("Click <a href=\"/LED=ON\">here</a> turn the LED on pin 2 ON<br>");
client.println("Click <a href=\"/LED=OFF\">here turn the LED on pin 2 OFF<br>");
client.println("</html>");

delay(1);
Serial.println("Client disconnected");
Serial.println("");
}
```
Connect GPIO 2 of the ESP8266 to the longer lead of the LED (+ve terminal). You can now control the LED remotely through the internet!

#### Running, Disconnection and powering:
Open the serial monitor and open the URL shown on your serial monitor through your web browser. 

![flowchart](/run1.png)

Click on the respective hyperlinks on your browser to toggle the LED ON and OFF.

![flowchart](/run2.png)

Now remove all the wires that were required for uploading. Lm1117 is used to provide regulated 3.3V output. It will let you make the ESP8266 or ESP-01 module stand alone.

![flowchart](/run3.jpg)

**Note:** Currently, the ESP8266 module can be accessed only through the local Wi-Fi network. To control your devices from the internet, you must perform port forwarding on your router. In order to do this, find the IP address of your system either by means of using the "ifconfig" command on your terminal, or going to whatsmyip.org. Then copy down your IP address. Open your router setting now and go to the "Forwarding" settings. Enter the details for the "Service Port" and "IP Address". Here, the IP address is the one you noted down before and the service port is the port number from your Arduino code (Service port: 80). Leave the other settings as default. Go to your browser now and enter the address: xxx.xxx.xx.xx:80 and this would open up the page for controlling the LED.

### Project Two: Receiving MPU6050 data over the Internet

#### Hardware and Software required
- ESP8266-01 board
- Arduino UNO board
- Jumper wires
- MPU6050 and its own Software requirements(the I2C and MPU6050 libraries)
- Arduino IDE

##### Working
The MPU6050 is a sensor capable of telling the inertial measurements (YPR- Yaw, Pitch, Roll) of the object on which it is mounted. We'll use Arduino IDE to program an MPU6050-ESP8266-UNO connection. The project shall follow the following course: uploading of bare minimum to ESP8266, then uploading the code for ESP8266 to read data from the serial pins (Tx and Rx) and sending it wirelessly to the computer, and then finally connecting MPU6050 to UNO. **UDP (User Datagram Protocol)**  is a communication protocol like TCP. TCP is a connection-oriented protocol and UDP is a connection-less protocol. TCP establishes a connection between a sender and receiver before data can be sent. UDP does not establish a connection before sending data. Hence each element of data is administered individually while sending and not through pre determined fixed data channels. We use UDP as it is easier to handle and faster. It is unreliable though due to errors which can be corrected through error rectifiers at the two ends. A port is a communication endpoint.

#### Uploading the Bare Minimum Code
The bare minimum is a code consisting of only two statements: void setup{} and void loop{}. The purpose is to reset the UNO board for uploading the esp.ino file to ESP8266-01 board through the UNO board. This is a necessary step before flashing and you can replace this step by using the procedure from the first project: using two push buttons.

![flowchart](/BareMinimum.png)

Installation of ESP8266 platform on Arduino IDE has already been discussed in the first project.

#### Connections and Uploading of the Main Code

![flowchart](/ESPconn1.jpg)

ESP - Arduino UNO
- Tx - Tx
- Rx - Rx
- VCC- 5V
- GND - 0V
- GPIO0 -0V
- CH_PD - 5V
- Arduino Reset- Arduino GND
Select Board as Generic ESP8266
Now copy the code given below to the Arduino IDE and press the upload button. Change SSID into your Wi-Fi access point name, and change the password to your Wi-Fi password and compile.
```
#include <ESP8266WiFi.h>
#include <WiFiUdp.h>

const char* ssid = "13:6";
const char* password = "123456789";
const char* udpAddress = "";          //IP address of your access point

const int udpPort = 3333;
String buff;

WiFiUDP udp;
void setup(){

Serial.begin(115200);
Serial.println();
Serial.printf("Connecting to %s ", ssid);

//initializing the wireless connection
WiFi.begin(ssid, password); //give the password and name for connection
while (WiFi.status() != WL_CONNECTED) {
delay(500);
Serial.print(".");
}
Serial.println(" connected"); 
Serial.printf("Web server started, open %s in a web browser\n", WiFi.localIP().toString().c_str());//c_str returns the pointer to the character array
}


//constantly read from the communication pins on UNO and send the read data via UDP to the IP address
void loop(){
if(Serial.available()){                   //if Serial communication ports of UNO are receiving data
buff = Serial.readStringUntil('\n');      //read the line containing YPR reading
char charBuf[buff.length() + 1];          //convert to character array
buff.toCharArray(charBuf, buff.length() + 1);   
udp.beginPacket(udpAddress,udpPort);      //open the channel to send data to the IP address at the port specific to the application being used-commonly for HTTP access, the port is 80
udp.printf("%s",charBuf);                 //initialize the packet with the readings from UNO
udp.endPacket();                          //close the channel
}
}
```
#### Making of MPU6050-ESP8266-UNO joint connection

![flowchart](/conn.jpg)

ESP8266 - UNO
- Tx - Rx
- Rx - Tx
- VCC- 5V
- GND - 0V
- GPIO0 -open
- CH_PD - 5V
- Remove Arduino Reset from Ground.

#### Execution
Download [MPUrequirements.rar](/MPUrequirements.rar) file.
Start Sending Data to Serial Monitor of the Arduino using sensor.ino file.
As we are using MPU6050, we need some extra libraries. Copy I2Cdev and MPU6050 to your libraies folder in Arduino.
Make connections according to conn.png.
Open MPU6050_DMP6 example from MPU6050 Library.
Make this file ready to output YPR data. Remove waiting condition and extra strings.
Typical Output Format >> pitch_tab_roll

#### Switch to internet and powering
After establishing wireless connection, switch to the hyperlink given on the serial monitor and disconnect the UNO. Now power the UNO through an external source. See the received data on the IP address.
You can also customize the data as shown below, by editing MPU6050 code.

![execution](/image-5.png)

## Some Important Observations
1. **Powering:** ESP8266-01 is designed for an operational voltage of 3.3v. However, all TTL based serial communication happens at 5V on Arduino board. So you need to downregulate the 5v voltage on UNO to 3.3v (using LM1117) on the wires starting from the Tx(for serial communication) and 5v(for power) pins of UNO.

2. **USB to TTL converter with DTR pin** can be used as a replacement for Arduino IDE to upload the code on ESP8266 to allow smooth upload of code (without using flash and reset buttons or bare minimum)

![flowchart](/TTL.jpg)

USB TTL ------> ESP8266 ESP-01
- GND------------>GND
- TX-------------->RX
- RX-------------->TX
- RTS------------->RST
- DTR------------->GPIO0

3. After obtaining the MPU readings, a Python code can run your favourite game and press the corresponding buttons according to the MPU readings.

## External references that may be read
- https://en.wikipedia.org/wiki/Transistor%E2%80%93transistor_logic
- https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter
- https://en.wikipedia.org/wiki/Serial_communication

## Bibliography
- https://maker.pro/esp8266/tutorial/esp8266-tutorial-how-to-control-anything-from-the-internet
- https://maker.pro/esp8266/tutorial/how-to-program-esp8266s-onboard-gpio-pins
- Ashok's git
- Wikipedia and Google
