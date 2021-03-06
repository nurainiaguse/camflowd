# Userspace Provenance Service

## Build Status

| Branch | Status                                                                                  | SonarQube |
|--------|-----------------------------------------------------------------------------------------|-----------|
| master | [![Master Build Status](https://api.travis-ci.org/CamFlow/camflow-service.svg?branch=master)](https://travis-ci.org/CamFlow/camflow-service/branches)  |[![SonarQube Status](https://sonarqube.com//api/badges/gate?key=camflow%3Amqtt)](https://sonarqube.com/dashboard?id=camflow%3Amqtt)   |
| dev    | [![Dev Build Status](https://api.travis-ci.org/CamFlow/camflow-service.svg?branch=dev)](https://travis-ci.org/CamFlow/camflow-service/branches)      |[![SonarQube Status](https://sonarqube.com//api/badges/gate?key=camflow%3Amqtt%3Adev)](https://sonarqube.com/dashboard?id=camflow%3Amqtt%3Adev)   |

Automated Travis test run the following operation:
- run [SonarQube](https://sonarqube.com).

## Configuration

The file `/etc/camflow-service.ini` allows to modify the configuration of the MQTT publisher service. The service need to be restarted for a new configuration to be applied (through `systemctl restart camflow-provenance.service`).

``` INI
[general]
; output=mqtt
output=log
log=/tmp/audit.log

[mqtt]
address=m12.cloudmqtt.com:17065
username=camflow
password=test
; message delivered: 0 at most once, 1 at least once, 2 exactly once
qos=2
```

## Checking logs

```
journalctl -b | grep camflowd
```
