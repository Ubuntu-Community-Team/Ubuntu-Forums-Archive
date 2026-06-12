---
title: "No wired or wireless networking w/ Gutsy upon install (Kubuntu)"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Jumboag99 on 2007-10-20
've got a Toshiba A105-S361 laptop.  Tried Feisty a few months back, it hated the laptop. Instant and repetitive KDE crashes, so went back to Gentoo.  Trying out Gutsy and its stable so far, but I have no networking whatsoever.

Both network interfaces are found, but I can't get an IP.  I prefer using wired when the laptop's at my desk for speed but I do flip between the two.  I'd like to try to tackle wired first, then get wireless working b/c I think that will be harder (I use WPA2 on wireless and I'm guessing its just a matter of figuring out where/how to set up wpa_supplicant's config for it in Kubuntu (vs gentoo).

I have a desktop as well (running Feisty - running it very well I might add). SO I can paste various config or module details for anybody that can help me out (Its a pain b/c I'll have to swing a flash drive between the boxes w/o networking, but I can do it.) 

If anybody can help me out, I'd appreciate it.  Just tell me what info you want me to post.  I'm not a exactly a Linux noob (used Gentoo for over a year) but I am very new to Kubuntu.

---

### Post by Pumalite on 2007-10-20
I have a collection of links that might help you. I hope:

[https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by Jumboag99 on 2007-10-20
Update:  Wired is now working.   I dont know why it fixes it, but adding "irqpoll" to my kernel bootup parameters got me running.  Now to figure out wireless.

---

### Post by Jumboag99 on 2007-10-20
Another update: I got wpa_supplicant running.  Now my problem is figuring out how to set up /etc/network/interfaces and /etc/default/ifplugd correctly for it to down my wireless and up the lan connection if I plug an ethernet cable in.

---

### Post by Pumalite on 2007-10-20
If you plug an ethernet cable, your wireless automatically disconnects

---

### Post by Jumboag99 on 2007-10-20
Even with Knetworking disabled?  (I had to disable it to use wpa_supplicant)

---

