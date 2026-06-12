---
title: "Where the hell is...."
date: 2013-11-18
forum: Installation &amp; Upgrades
---

### Post by jstratta on 2013-11-18
Im trying to mess with (install) broadcom drivers for wireless. Im following all the steps correctly. It seems the directory its telling me to go to does not exist "pool/main/p/patch" it and it most certainly does not. There is no place for that on my image. Where can i get all of the files i need and why arent they in the image i downloaded. Im trying to install STA without internet from here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers).  PS i have a HP MINI 1000.

---

### Post by Old_Grey_Wolf on 2013-11-18
Can you plug in an Ethernet cable in the HP MINI 1000?

[s]What version of Ubuntu are you using?[/s]

Edit: I see from the tags that you are using 12.04.03.

---

### Post by jstratta on 2013-11-18
No, it has no Ethernet ports. I have to do the Non internet way but get stuck at the part where it tells me to go to p/patch because it does not exist on the 12.04 cd.

---

### Post by Old_Grey_Wolf on 2013-11-18
See if this link works better than the one you have been using. [https://help.ubuntu.com/community/BroadcomSTA(Wireless)](https://help.ubuntu.com/community/BroadcomSTA(Wireless))

---

### Post by jstratta on 2013-11-20
This did not help as i have a chip id 4312 with pciid 4315 without internet and it does not explain what to do.

---

### Post by jstratta on 2013-11-20
I followed post 5 from here [http://ubuntuforums.org/showthread.php?t=2168816](http://ubuntuforums.org/showthread.php?t=2168816) a second time. It recognizes the wifi adapter but it does not scan for networks. When i put in the info manually by clicking connect to hidden network it can connect. How do i make it so it scans for networks automatically and so i dont have to type in info each time for a new wifi network

---

### Post by jstratta on 2013-11-20
OK SO NOWWWWWWWWWW i reinstalled everything with a new 12.04 ubuntu. Did the instructions a third time but without rmmod because it said it couldnt find the modules. Did an apt-get update and upgrade and it installs the wl driver over top of it and can now scan for networks on its own.

---

### Post by jstratta on 2013-11-20
Thank you for your help and cooperation.

---

### Post by coffeecat on 2013-11-20
> **jstratta said:**
> No, it has no Ethernet ports. 

I know you've solved your wireless problem now, but are you sure? My HP Mini has an ethernet port but it's somewhat camouflaged with a dust cover.

---

