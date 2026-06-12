---
title: "firestarter problem"
date: 2005-09-01
forum: Installation &amp; Upgrades
---

### Post by Ubuntu_User on 2005-09-01
I installed Firestarter to share my internet connection with the other computers on our home network, but when i start firestarter, i fails and gives a message like that:

"The device eth0 is not ready"

But when i go System->Administration->Network it shows the eth0 active.


Can someone help me with that problem?

---

### Post by KingBahamut on 2005-09-01
Can you output your ifconfig in here. 

also, have you tried deactivating and activating the interace , then retrying?

---

### Post by FLeiXiuS on 2005-09-01
If your using DHCP try releasing your lease.  

```

$sudo dhclient -r eth0

```

Then renew a lease.

```

$ sudo dhclient eth0

```

---

### Post by Ubuntu_User on 2005-09-01
The result of ifconfig is that:

```
eth0      Link encap:Ethernet  HWaddr 00:11:D8:27:66:AF
          inet6 addr: fe80::211:d8ff:fe27:66af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1551 (1.5 KiB)  TX bytes:2602 (2.5 KiB)
          Interrupt:17 Memory:d7efc000-0

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:706413 (689.8 KiB)  TX bytes:706413 (689.8 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:212.205.226.191  P-t-P:62.103.2.243  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:212659 (207.6 KiB)  TX bytes:33198 (32.4 KiB)
``` 

and after releasing my lease as FLeiXiuS said i got that:

```
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

ppp0: unknown hardware address type 512
sit0: unknown hardware address type 776
ppp0: unknown hardware address type 512
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:11:d8:27:66:af
Sending on   LPF/eth0/00:11:d8:27:66:af
Sending on   Socket/fallback
root@pcfot:/home/fotis # sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

ppp0: unknown hardware address type 512
sit0: unknown hardware address type 776
ppp0: unknown hardware address type 512
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:11:d8:27:66:af
Sending on   LPF/eth0/00:11:d8:27:66:af
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by Ubuntu_User on 2005-09-02
Can someone help me?

---

### Post by FLeiXiuS on 2005-09-02
Go into the firestarter config from the GUI and change the interface.  Your not using eth0 so of course it wouldn't be ready.  Your using ppp0.  So make the changes then restart firestarter.

---

### Post by Ubuntu_User on 2005-09-02
In Firestarter's settings i have over the network settings:

**Internet Connected Network Device:**
DialUp Service (ppp0) *[which is the one that i want to share]*

**Local Network Connected Device:**
ETHERNET Device (eth0)

I have the same problem!
When i start Firestarter fails and gives a message: "eth0 is not ready"

Please help me

Thanx in Advance

---

### Post by Ubuntu_User on 2005-09-02
up...

---

### Post by Ubuntu_User on 2005-09-04
Please, help me somebody...  :-|  :roll:

---

