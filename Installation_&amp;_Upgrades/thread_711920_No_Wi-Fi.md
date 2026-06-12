---
title: "No Wi-Fi"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by Carb0neum on 2008-03-01
Hello,

Finally i'm using Ubuntu, but when i boot Vista my Wi-Fi works fine / when i boot Ubuntu 7.10 the Wi-Fi don't work.

               Specs:
     Packard Bell Easynote SJ51 New 3
Monitor:             17" TFT widescreen Diamond View (connection DVI-I)
Video kaart:       nVidia GeForce GO 7000m
Video geheugen:Max 751 MB Turbo Cache
Geluid:              Soundblaster Compatible
Netwerk:            Lan en Wifi
OS:                   Vista Home Premium // Ubuntu 7.10
Geheugen:         2GB DDR
Hardeschijf:       160GB
Processor:         AMD Athlon&#8482; 64 X2 processor TK-55 Dual-Core
Kloksnelheid:     1,80Ghz
Netwerkkaart:    10/100 LAN Ethernet
Wi-Fi:                 802.11 b/g

My networkadapters (like vista say):
- nVidia nForce Networking Controller
- Realtek / Realtec RTL8187b Wireless 802.11b/g 54 Mbps USB 2.0 Netwerking adapter
          Windows driver: C:\Windows\system32\rtl8187b.sys

Wat i already have tried
- Ndiswrapper >  [http://paste.ubuntu-nl.org/57792/](http://paste.ubuntu-nl.org/57792/), iWindows version from the official site
- A alternative driver from somewhere on the ubuntu wiki
- Mutch use of google

Hopefully can one of u help me,

Rik Huyzer.

---

### Post by Pumalite on 2008-03-01
Post:
lshw -C network

---

### Post by Carb0neum on 2008-03-01
> **Pumalite said:**
> Post:
lshw -C network

[http://paste.ubuntu-nl.org/57963/](http://paste.ubuntu-nl.org/57963/)

---

### Post by Pumalite on 2008-03-01
OK. go to the Terminal and type:
alsamixer
Tell me what you see.
( a screenshot would be great)

---

### Post by Carb0neum on 2008-03-01
> **Pumalite said:**
> OK. go to the Terminal and type:
alsamixer
Tell me what you see.
( a screenshot would be great)

[[IMG]http://img257.imageshack.us/img257/7229/screenshot1eh5.th.png[/IMG]](http://img257.imageshack.us/my.php?image=screenshot1eh5.png)

---

### Post by Carb0neum on 2008-03-01
[http://ubuntuforums.org/search.php?searchid=37158660](http://ubuntuforums.org/search.php?searchid=37158660) < w00ps this is not the first post about the realtek card, but even the solved one [http://ubuntuforums.org/showthread.php?t=708605&highlight=rtl8187b](http://ubuntuforums.org/showthread.php?t=708605&highlight=rtl8187b) don't work for me...

---

### Post by Pumalite on 2008-03-01
First of all make all the volumes in alsamixer 100%

---

### Post by Carb0neum on 2008-03-01
> **Pumalite said:**
> First of all make all the volumes in alsamixer 100%

That gonna solve my problem?

---

### Post by Pumalite on 2008-03-01
Could be. The next thing would be to compile the latest alsa-driver

---

### Post by Pumalite on 2008-03-01
Here is for your perusal:
From other threads:
Wireless:

[http://ubuntuforums.org/showthread.php?t=618596&page=2](http://ubuntuforums.org/showthread.php?t=618596&page=2)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
[http://ubuntuforums.org/showthread.php?t=586387](http://ubuntuforums.org/showthread.php?t=586387)
[https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
[http://ubuntuforums.org/showthread.php?t=612065](http://ubuntuforums.org/showthread.php?t=612065)

---

### Post by Carb0neum on 2008-03-01
The driver is working and in the network tool (graphical) there stands wire-less connection and the name of the network that is the same network i have on Vista. Prob solved!

---

### Post by Pumalite on 2008-03-01
Ok.

---

