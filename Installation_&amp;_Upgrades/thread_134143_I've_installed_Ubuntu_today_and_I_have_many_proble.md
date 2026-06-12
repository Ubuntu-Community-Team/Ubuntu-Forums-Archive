---
title: "I've installed Ubuntu today and I have many problems... please help!"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by Starlight on 2006-02-21
Hi!

I've installed Ubuntu today as my second operating system. But I have some problems with it. :( 

First of all, the installer couldn't detect my internet connection. I tried again a few times, but it didn't work. I have a cable modem with DHCP and it works automatically in Windows. 

Second, the only available screen resolution seems to be 640 x 480 and I can't change it. I have a LCD display with 1280 x 1024 default, so it looks really bad...

Third, I wanted to install the 3D ATI video card drivers (I have Radeon 9550), but there was no xorg-driver-fglrx in the Miscellaneous - Graphical (Restricted) category.

Please help me... I'd really love to start using Ubuntu, but I just can't do it if I don't have internet connection and the screen resolution is so low :(


edit: if it could help you find out what's wrong with my Ubuntu, I'll post what "ifconfig eth0" and "dhclient eth0" say.....

---

### Post by el3ktro on 2006-02-21
Which type of network card do you have?

Tom

---

### Post by Starlight on 2006-02-21
Hi, Tom!

It's a network card on the nForce2 motherboard...

---

### Post by rjwood on 2006-02-21
The first thing I would look at for your internet connection is system>admin>network tools...make sure etho is active--if not activate it.

For you resolution ```
sudo dpkg-reconfigure xorg.config
```
have your monitor info handy and let x read your hardware. When you get top the monitor, you can input the info for it. X should also set your vidio driver or give you options for it.

Good Luck!!!

Welcome to Ubuntu:-D

---

### Post by heimo on 2006-02-21
[quote=rjwood]
For you resolution ```
sudo dpkg-reconfigure xorg.config
``` [/quote]

You meant to write:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Starlight on 2006-02-21
Thanks for the welcome, rjwood :)

And thanks for the advice...I'll try to do it. :) 

And I've already tried activating it. After a few minutes of waiting, it gets activated, but internet still doesn't work....

---

### Post by el3ktro on 2006-02-21
Please look at the output of "ifconfig" in the Terminal if you get an IP address from the DHCP server. NForce2-NICs are definitely supported in Linux.

Tom

---

### Post by Starlight on 2006-02-21
I have a high resolution now! :D 

But network still doesn't work... here's what ifconfig says:

[COLOR="RoyalBlue"]~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:A4:6D:C0
          inet6 addr: fe80::20c:6eff:fea4:6dc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:512540 (500.5 KiB)  TX bytes:6876 (6.7 KiB)
          Interrupt:22 Base address:0xa000 [/COLOR]


and dhclient

[COLOR="RoyalBlue"]~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:0c:6e:a4:6d:c0
Sending on   LPF/eth0/00:0c:6e:a4:6d:c0
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
ip length 330 disagrees with bytes received 334.
accepting packet with data after udp payload.
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping. [/COLOR]

:confused:

---

### Post by rjwood on 2006-02-21
[quote=heimo]You meant to write:
```
sudo dpkg-reconfigure xserver-xorg
```[/quote]

OOps thanks heimo! wasn't thinking straight!!!

---

### Post by Starlight on 2006-02-22
Bump....


Should I post it in the networking forum? :confused:

---

### Post by jchau on 2006-02-22
Your networking problem seems to be either caused by either your cable modem (sending bad info) or your dhcp client not knowing how to interpret what your cable modem sends.  try running your command with dhclient3 instead of dhclient:
```
sudo dhclient3 eth0
```

if that doesn't work, try:
```
sudo ifdown eth0
sudo ifup eth0
```

Sometimes, if the network cable is not plugged in when the computer starts, the network will not work. (Dunno if this is your problem)

---

### Post by Starlight on 2006-02-22
Thank you! :) I'll try that... I've also found out that I have a custom MAC address set in Windows, which is different than the one in Linux. Maybe my ISP recognizes only that one? Is there a way to set a custom MAC address on Ubuntu?

---

