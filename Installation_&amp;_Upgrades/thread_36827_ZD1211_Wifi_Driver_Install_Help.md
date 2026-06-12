---
title: "ZD1211 Wifi Driver Install Help"
date: 2005-05-24
forum: Installation &amp; Upgrades
---

### Post by malachakla on 2005-05-24
Hi,
Could anyone guide me through installing these drivers on Ubuntu?
I really  have no clue. 
Thanks very much!

---

### Post by f.prisson on 2005-05-25
Have a look at this, but maybe not that simple:

[http://sourceforge.net/projects/zd1211](http://sourceforge.net/projects/zd1211)

---

### Post by malachakla on 2005-05-25
Got the driver installed and compiled, and the USB Wlan finds my access point, but it won't connect to the internet!
When I ping the address I ping is always unknown.
The adapter is active in the networking preferences and all necessary information is filled in.
Thanks for the driver!

---

### Post by f.prisson on 2005-05-26
Please post the output of```
iwconfig
``` ```
ifconfig
``` ```
route -n
``` then I can tell you more.

---

### Post by malachakla on 2005-05-26
**iwconfig:** 
lo        no wireless extensions.

eth0      802.11b/g NIC  ESSID:"20371GillickWay"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:0D:72:53:68:59
          Bit Rate:1 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Encryption key:****-****-**   Security mode:open
          Power Management:off

eth1      no wireless extensions.

sit0      no wireless extensions.

**ifconfig:** 
root@mantra:/home/jonathan # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:A3:00:1D:ED
          inet6 addr: fe80::211:a3ff:fe00:1ded/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:761 (761.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4687 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:366977 (358.3 KiB)  TX bytes:366977 (358.3 KiB)

**route -n:** 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

Hope this helps!
Thanks!

---

### Post by f.prisson on 2005-05-27
OK, your connection to your AP is active, although it's not the best with 1 MBit.
You have no IP configured, that's the problem.

Go to System -> Management -> Network and configure the appropriate settings for your environment.

---

### Post by malachakla on 2005-05-27
By "proper settings", do you mean the ESSID and encryption key and selecting "DHCP" or "Static IP"?
If so, I've already done so.

---

### Post by f.prisson on 2005-05-28
OK, the settings for the WLAN are accepted.
Try the settings for the IP configuration in bash. Type```
sudo dhclient eth0
``` for receiving a DHCP address or set a static one with```
sudo ifconfig eth0 x.x.x.x up
``` and try to ping your AP.

---

### Post by malachakla on 2005-05-28
I tried the prompt for recieving the DHCP address, and the system appears to assign an IP address:
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:11:a3:00:1d:ed
Sending on   LPF/eth0/00:11:a3:00:1d:ed
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 172.16.0.1
bound to 68.124.205.254 -- renewal in 233 seconds.

But pings are unknown and I still cannot connect to the Internet.

---

### Post by f.prisson on 2005-05-28
And after that ifconfig shows no ip adress? I'm a little confused because you receive an IP adress 68.124.205.254 from a DHCP server with adress 172.16.0.1

---

### Post by ant_dot on 2005-06-15
Hi,

I had also the same problem as yours. But then I deactivate the network card, so when I want to use wlan, I activate only the wlan interface. As a result, I am now able to access internet. :)

---

### Post by freedomfighter on 2005-07-30
[QUOTE=malachakla]Got the driver installed and compiled, and the USB Wlan finds my access point, but it won't connect to the internet!
When I ping the address I ping is always unknown.
The adapter is active in the networking preferences and all necessary information is filled in.
Thanks for the driver![/QUOTE]

You didn't say how you compiled the driver. I managed to compile the driver from source but it wasn't obvious since i did it from a PC without a net connection. Here is a brief summary of my steps:
1. sudo apt-get install debhelper build-essential fakeroot linux-headers-$(uname -r)
2. extract the .tar.gz file to ~/ (tar zxvf sf_zd1211_20050315_src.tar.gz)
3. cd ~/zd1211
4. sudo ln -s /lib/modules/$(uname -r) /lib/modules/2.6.10
5. make KSRC=/usr/src/linux-headers-$(uname -r)
6. sudo make KSRC=/usr/src/linux-headers-$(uname -r) install

Follow the README file in ~/zd1211 for further instructions.

---

### Post by brousch on 2005-08-02
I put up a wiki with Ubuntu-specific instructions for the zd1211
[https://wiki.ubuntu.com/zd1211wifi](https://wiki.ubuntu.com/zd1211wifi)

---

### Post by jr_G-man on 2005-08-27
I'm having my own issues with getting this installed and working.  I have a blog entry describing my experiences so far.  It's located here:  [http://www.bloglines.com/blog/jrgman?id=5](http://www.bloglines.com/blog/jrgman?id=5)

I have an update.  I'll notify when I post it.

---

