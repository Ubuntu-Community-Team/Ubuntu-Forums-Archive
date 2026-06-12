---
title: "failed internet connection on installation of 6.10"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by the edge on 2007-05-20
Greetings all
First time installation of Linux ,that being Ubuntu 6.10
With the folllowing settings i still cannot connect to the internet despite spending considerable time in various forums looking for assistance.
 
Duel boot system with Ubuntu and windows xp both are operating correctly
Netcomm Nb5 Adsl2 Modem Router with an ethernet connection which connects perfectly to the net. 
All lights are operating on front of modem except usb

Under System-Admin-Networking, the following information has been entered as under windows xp profile

I.P address: 192.168.1.100
Subnet mask:  255.255.255.0
Default Gateway: 192.168.1.1

Enabled box has been ticked.

Firefox settings-preferences: Connected directly to internet.

Please provide any other settings or set up installations that are required much appreciated
 thank you/Mark

---

### Post by aliyanage on 2007-05-20
Hi,

did you already try using DHCP?

besides that what output do you get if you open a terminal and write the command:

```
ifconfig
```

regards
aliyanage

---

### Post by the edge on 2007-05-20
Thanks for reply sorry for delay,retried using dchp settings no luck, firefox will not establish connection.
the two attached documents show ifconfig details under dchp or static ip address under networking.
pls excuse ignorance having trouble finding reply posts whats the easiest way to follow the threads to my post from log in page/Mark

---

