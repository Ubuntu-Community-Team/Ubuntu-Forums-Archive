---
title: "[SOLVED] Wireless does not automatically connect on boot"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wilsong on 2008-09-30
Hello, I am running Ubuntu 8.10 Alpha 6, 

I have had ubuntu start and ask me to enter the WEP key, for the wireless but i would like to have it auto connect, when i try to set it up for auto connecting, it doesnt connect and it always seems that i have to go into Network Connections, Wireless, and click on Auto (My Wireless Routers SSID here) and it says 9 hours ago (last time i connected i suppose) 

When i edit that, it says "auto ssid" 

I have checked Connect Automatically , I checked System setting (i am a little confused on what this does, but i am wanting it to always find and connect to this device anytime its in range.. 

When i set the wireless ssid its already correct, 
Mode Infrastructure 
MTU auto

BSSID blank
MAC blank 

Wireless Security WEP 40/128-Bit key

I use a 128bit key, i click show key, and type it in.. 

Wep index 1 Autho Open system,

I set IPv4 to the settings i use, and i have also tried to do Auto DHCP, 

the only problem, it will connect, but when i reboot, i start again it doesnt automatically connect, i always have to reenter the ssid wither in the popup box that comes up when i boot, or having to go into Network connections. 

Please help! Thanks

I just kept entering the correct settings and now its working so i hope it will keep up

---

### Post by Tatty on 2008-09-30
It may be best to ask this in the intrepid development forum:
[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)


Intrepid is still in development and so many bugs may remain, If no one can help you in the intrepid forum then you can help out development by posting a bug report, or adding information to an existing one.

---

### Post by Crafty Kisses on 2008-09-30
What are the results of this command?```
lshw -C network
```

---

### Post by wilsong on 2008-09-30
*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:7b:22:0b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1b:fc:44:99:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.92 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: a6:f9:c0:c8:fb:9f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by wilsong on 2008-09-30
> **Codename said:**
> What are the results of this command?```
lshw -C network
```

Any more ideas?

---

### Post by wilsong on 2008-09-30
> **Tatty said:**
> It may be best to ask this in the intrepid development forum:
[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)


Intrepid is still in development and so many bugs may remain, If no one can help you in the intrepid forum then you can help out development by posting a bug report, or adding information to an existing one.

I asked in that forum and haven't had a response, any ideas?

---

