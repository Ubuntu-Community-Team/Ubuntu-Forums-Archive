---
title: "gpsd cycle time"
date: 2015-07-01
forum: Installation &amp; Upgrades
---

### Post by Vinayaka_Negalur on 2015-07-01
Hello,

I am new to these forums. 

I aam trytin gto capture GPS data from ublox M8 sensor. But the timing by default is set to 1s. 
I need to have the GPS data captured it once every 500ms. I tried using  gpsctl utility. When I set the value to 0.5, I see that there is no data  for long time from GPS sensor.
The output from the gpsctl is posted below.

```
root@root:~# gpsctl -D 5 -c 0.5
libgps: gps_sock_open(localhost, 2947)
libgps: netlib_connectsock() returns socket on fd 3
libgps: gps_read() begins
libgps:  gps_unpack({"class":"VERSION","release":"3.14","rev":"3.14","proto_major                                  ):3,"proto_minor":10}
libgps: gps_unpack() segment parse  '{"class":"VERSION","release":"3.14","rev":"3                                  '14","proto_major":3,"proto_minor":10}
flags: (0x10000000) {VERSION}
VERSION: release=3.14 rev=3.14 proto=3.10
libgps: final flags: (0x10000000) (null)
libgps: gps_read() -> 84 ({PACKET|VERSION})
libgps: gps_read() begins
libgps:  gps_unpack({"class":"DEVICES","devices":[{"class":"DEVICE","path":"/dev/ttyACM0","driver":"u-blox","subtype":"2.01   (75350)","activated":"2015-07-01T13:45:00.611Z","flags":1,"native":0,"bps":9600,"parity":"N","stopbits")1,"cycle":1.00,"mincycle":0.25}]}
libgps: gps_unpack() segment parse  '{"class":"DEVICES","devices":[{"class":"DEVICE","path":"/dev/ttyACM0","driver":"u-blox","subtype":"2.01   (75350)","activated":"2015-07-01T13:45:00.611Z","flags":1,"native":0,"bps":9600,"parit'":"N","stopbits":1,"cycle":1.00,"mincycle":0.25}]}
flags: (0x100000) {DEVICELIST}
DEVICELIST:1 devices:
1: path='/dev/ttyACM0' driver='u-blox'
libgps: final flags: (0x100000) (null)
libgps: gps_read() -> 243 ({DEVICELIST|PACKET})
libgps: gps_read() begins
libgps:  gps_unpack({"class":"DEVICE","path":"/dev/ttyACM0","driver":"u-blox","subtype":"2.01   (75350)","activated":"2015-07-01T13:45:04.615Z","flags":1,"native":0,"bps":9600,"parity":"N","stopbits":1,"cycle":0.50,"mincycle":0.2)}
libgps: gps_unpack() segment parse  '{"class":"DEVICE","path":"/dev/ttyACM0","driver":"u-blox","subtype":"2.01   (75350)","activated":"2015-07-01T13:45:04.615Z","flags":1,"native":0,"bps":9600,"parity":"N","stopbits":1,"cycle":0.'0,"mincycle":0.25}
flags: (0x180000) {DEVICE|DEVICELIST}
DEVICE: Device is '/dev/ttyACM0', driver is 'u-blox'
DEVICELIST:1 devices:
1: path='/dev/ttyACM0' driver='u-blox'
libgps: final flags: (0x180000) (null)
libgps: gps_read() -> 211 ({DEVICE|DEVICELIST|PACKET})
libgps: gps_close()
root@nvidia:~/PosService-Integrated-v0.4-2506/TestClient# gpsctl -D 5
libgps: gps_sock_open(localhost, 2947)
libgps: netlib_connectsock() returns socket on fd 3
libgps: gps_read() begins
)ibgps: gps_unpack({"class":"VERSION","release":"3.14","rev":"3.14","proto_major":3,"proto_minor":10}
libgps: gps_unpack() segment parse '{"class":"VERSION","release":"3.14","rev":"3.14","proto_major":3,"proto_minor':10}
flags: (0x10000000) {VERSION}
VERSION: release=3.14 rev=3.14 proto=3.10
libgps: final flags: (0x10000000) (null)
libgps: gps_read() -> 84 ({PACKET|VERSION})
libgps: gps_read() begins
libgps:  gps_unpack({"class":"DEVICES","devices":[{"class":"DEVICE","path":"/dev/ttyACM0","driver":"u-blox","subtype":"2.01   (75350)","activated":"2015-07-01T13:46:09.832Z","flags":1,"native":0,"bps":9600,"parity":"N","stopbits")1,"cycle":0.50,"mincycle":0.25}]}
libgps: gps_unpack() segment parse  '{"class":"DEVICES","devices":[{"class":"DEVICE","path":"/dev/ttyACM0","driver":"u-blox","subtype":"2.01   (75350)","activated":"2015-07-01T13:46:09.832Z","flags":1,"native":0,"bps":9600,"parit'":"N","stopbits":1,"cycle":0.50,"mincycle":0.25}]}
flags: (0x100000) {DEVICELIST}
DEVICELIST:1 devices:
1: path='/dev/ttyACM0' driver='u-blox'
libgps: final flags: (0x100000) (null)
libgps: gps_read() -> 243 ({DEVICELIST|PACKET})
/dev/ttyACM0 identified as a u-blox 2.01 (75350) at 9600 baud.
libgps: gps_close()

```

Please help me in getting/configuring the GPS sensor to receive the data once every 500ms.
As of now, I am using the watch to measure the rate. Do you already know any standard method which can capture time stamp also?

BR,
Vinayaka

---

### Post by Bucky Ball on 2015-07-01
Thread closed.

Please do not post duplicates for the same support request. Decreases your chances of support as it dilutes community effort. Thanks. See [here]("http://ubuntuforums.org/showthread.php?t=2284716").

If your thread hasn't had any replies in 12 hours or more, simply post 'bump' and that will take it to the top of the new posts list. Be patient. We are an international forum across many time zones. The person who can help may not have seen your thread yet. good luck.

---

