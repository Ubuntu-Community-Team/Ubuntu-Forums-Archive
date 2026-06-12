---
title: "No network in ubuntu 10.4"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by kishoreru on 2010-04-30
Hi 
 I just install ubuntu 10.04 in my Dell vostro 1500 laptop. I am not able to access the network both wireless and wire networks are not working in it
My wireless network adapter is Dell wireless 1395 WLAN Mini-card and wire network adapter is Broadcom 440x10/100 


Please help me in solve the problem

---

### Post by arunkumarra on 2010-05-01
me too dude.. pls help..

---

### Post by uvsc2010 on 2010-05-03
To get the wire connection to work on vostro 1500:
Install version 9.1 ubuntu studio first, the wire connection will work.  Than do the upgrade using Upgrade Manager to 10.04
 
To get the wireless adapter installed on vostro 1500:
Follow the steps from above, than use "System"->"Administration"->"Hardware Drivers"
First activate Broadcom B43 wireless driver
Than activate Broadcom STA wireless driver
 
Next from the Ubuntu Software Center
install "WiFi Radar"
 
That's all I got so far, I was able to list all the WiFi access points available, I am still trying to figure out how to put the connect parameters in.

---

### Post by infamous-online on 2010-05-03
Or go to Dell and see if they have the wireless drivers for linux. My Vostro and Latitude laptops didn't need the drivers as they were recognized. So go there to see if they them, Dell does do support for Ubuntu.

---

