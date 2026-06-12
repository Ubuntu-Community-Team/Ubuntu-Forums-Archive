---
title: "wireless problem ubuntu 7.10"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by bskafh on 2007-10-20
hi, I am having a problem with my wireless. i just upgraded to ubuntu 7.10 and i cant see any wireless connections. I can't even see the wireless device. when i go to network connections i can only see wired and modem connections. I alos can't find the device manager. I know its a busy time, but i went through previous posted and i couldn;t find anyone with this problem. Thanks a lot guys in advanced.

---

### Post by Ba66e77 on 2007-10-20
Try this: 

[http://ubuntu1501.blogspot.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html](http://ubuntu1501.blogspot.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by bskafh on 2007-10-20
Thanks for the link, but i cant find System>Administration>Restricted Driver Manager. is there a way to run the device manager form the terminal?

---

### Post by bskafh on 2007-10-20
anyone?

---

### Post by bskafh on 2007-10-21
hello!!

---

### Post by bobyy on 2007-10-22
Hello 
first run #lspci  to see if your wirelles dev. is listed here.
if is here from the repository install Ndiswrapper 
now you need your windows driver from wirelles card (put in some folder)
#ndiswrapper      and you will se the commands for Ndiswrapper.
 from that folder were you put the driver run:
#ndiswrapper  -l  xxxx.inf  (xxxxx.inf   replace xxxxx.inf with real name of file )
if you have no error run
#ndiswrapper -m   to load the module in kernel
now you will have your wirelles device and you can config him with 
#iwconfig ath0 essid xxxxx (xxxx your network)
#iwconfig ath0  mode managed
#iwconfig ath0  key xxxxx
#dhcpcd ath0

good luck.

---

### Post by bskafh on 2007-10-22
hi i have the fujitsu a6010 with a built in  Intel 3945 802.11 a/b/g card. its not an external card. will this also work?

---

### Post by bobyy on 2007-10-22
Hy
if you have the win driver and install Ndiswrapper it will work.. :) 
please let` me know ti is work or not...

---

### Post by bskafh on 2007-10-22
thanks you but where can i find my driver files in windows?

---

### Post by bobyy on 2007-10-22
if you know the wireless device model just download`it from internet......and uset`it...it is no necessary the driver, witch is phisicalli instaled on windows partition....

---

