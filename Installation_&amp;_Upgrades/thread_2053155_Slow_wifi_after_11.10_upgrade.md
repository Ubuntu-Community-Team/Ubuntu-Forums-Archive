---
title: "Slow wifi after 11.10 upgrade"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by gtdcubo on 2012-09-04
After having upgraded from 10.10 to 11.10 via 11.04 my wifi response times have changed from very fast to "dial up" slowness.

Two days ago I opened a [thread]("http://ubuntuforums.org/showthread.php?t=2052145") which no one answered, perhaps because I tried to give too much information.

This time I will keep it minimalist.

Before 10.10 => fast wifi
Now 11.10 => slow wifi

Please help  me diagnose and solve this, as it has ruined my enjoyment of Ubuntu.

---

### Post by gtdcubo on 2012-09-04
Well that didn't attractt much attention. I have now read the section on Internet problems and will shortly post some output from my system. I will hope that this may elicit a response to my problem.

---

### Post by gtdcubo on 2012-09-04
This page suggests that the following info may help with diagnosis of my problem. 

[http://askubuntu.com/questions/14008/i-have-a-hardware-detection-problem-what-logs-do-i-need-to-look-into](http://askubuntu.com/questions/14008/i-have-a-hardware-detection-problem-what-logs-do-i-need-to-look-into)

```
paul@VLC-GF7050VT-M:~$ sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:1e:90:63:9f:ac
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:44 memory:fe9f7000-fe9f7fff ioport:c880(size=8) memory:fe9fe800-fe9fe8ff memory:fe9fe400-fe9fe40f
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: 00:12:17:96:81:20
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2500usb driverversion=3.0.0-24-generic-pae firmware=N/A ip=192.168.1.33 link=yes multicast=yes wireless=IEEE 802.11bg

```

```
paul@VLC-GF7050VT-M:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13b1:000d Linksys WUSB54G v4 802.11g Adapter [Ralink RT2500USB]
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 006: ID 1d0d:0214  
Bus 002 Device 002: ID 046d:0928 Logitech, Inc. QuickCam Express
Bus 002 Device 003: ID 15d9:0a33 Trust International B.V. Optical Mouse
```

I am hoping that with this info someone might suggest where I can begin to diagnose and solve this problem.

Thanks for the attention

---

### Post by gtdcubo on 2012-09-08
**Re: Slow wifi after 11.10 upgrade**
Oops this  problem of this upgrade is not attributable to 11.10 upgrade as such,  but the following. There was slowness at first during which I deleted  and recreated the network connection. But in doing so I forgot that I  use open DNS and not the native DNS servers of my ISP. In resetting up  the connection I neglected to use Open DNS, and therefore the solution  to the slowness - which was most probably solved by one of my  interventions at the terminal prompt - remained obfuscated. As soon as I  edited the connection to use Open DNS I found that network response  times returned to satisfactory levels. 

Here is a the article that reminded me about Open DNS

[http://askubuntu.com/questions/66989...-network-speed]("http://askubuntu.com/questions/66989/ubuntu-11-10-network-speed") 

Go down to the reply by José C Alavez 26/10/11 at 01:27

---

