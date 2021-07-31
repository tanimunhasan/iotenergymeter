#include<ThingSpeak.h>
#include<ESP8266WiFi.h>
#include<WiFiClient.h>
#include<ESP8266WebServer.h>
//#include <PZEM004Tv30.h>
//PZEM004Tv30 pzem(D1,D2); //RX/TX
const char* ssid = " ";//
const char* password = "*****";
String apiKey = "*****";    

//WiFiClient client;
const char* server = "api.thingspeak.com"; //eg: 192.168.0.222
float voltage,current,pf,frequency,power;
int a=0,b=0;

WiFiClient client;


void setup()
{
 Serial.begin(115200);
  delay(10);
//  dht.begin();
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
// server.begin();
  Serial.println("Server started");
  Serial.print(WiFi.localIP());
  delay(1000);
  Serial.println("connecting...");
 }
void loop()
{

  voltage = (analogRead(A0));//pzem.voltage();
  current =.80;// pzem.current();
  power = voltage*current;//pzem.power();
  //power=power/1000;
  frequency = 50;//pzem.frequency();
  pf = 1;//pzem.pf();

  for (a=0;a<=100;a++)
  {
//    server.handleClient();
    delay(100);      
  }
   Sending_To_thingspeak();    
}
void Sending_To_thingspeak() //CONNECTING WITH MYSQL
 {
   if (client.connect(server, 80)) {
    Serial.println("connected");
    // Make a HTTP request:
    Serial.print("GET /update?api_key=P3CGQ306SBV4XVPE&field1=0");
    client.print("GET /update?api_key=P3CGQ306SBV4XVPE&field1=0"); //YOUR URL
    Serial.println(voltage);

    client.print(voltage);
 
    client.print("&field2=");
    Serial.println("&field2=");
   
    client.print(current);
    Serial.println(current);

    client.print("&field3=");
    Serial.println("&field3=");
   
    client.print(power);
    Serial.println(power);

    client.print(" "); //SPACE BEFORE HTTP/1.1
    client.print("HTTP/1.1");
    client.println();
    client.println("Host: api.thingspeak.com");
    client.println("Connection: close");
    client.println();
  } else {
    // if you didn't get a connection to the server:
    Serial.println("connection failed");
  }
 }
