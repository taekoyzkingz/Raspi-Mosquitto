# How to Install MQTT Broker(Mosquitto) in Raspberry PI

- Check Software Mosquitto
```bash
$ sudo apt-cache search mosquitto
```
- Install Mosquitto, Mosquitto Client and Library Mosquitto Dev
```bash
$ sudo apt install mosquitto mosquitto-clients libmosquitto-dev
```
- Edit Config File
```bash
$ sudo nano /etc/mosquitto/mosquitto.conf
```
- To add the Following
```bash
# default listener
port 1883
# additional listener for websockets
listener 9001
protocol websockets
allow_anonymous false
password_file /etc/mosquitto/passwd
```
- Create Username & Password of Broker
```bash
$ sudo mosquitto_passwd -c /etc/mosquitto/passwd "username"
```
- Restart Service
```bash
$ sudo service mosquitto restart
```
- Check Status Service
```bash
$ service mosquitto status
```
- Test Mosquitto
```bash
$ mosquitto_pub -d -h localhost -p 1883 -u "username" -P "password" -q 1 -t "topic" -m "message"
```
