---
title: "Problems Installing ATI fglrx driver Edgy"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by FlamingBee on 2007-04-18
Hey all. Right, i've been trying to install the ATI fglrx driver for Ubuntu, so i can get 3D Acceleration on my X850 Pro (Unlocked). At first, i followed method one on this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) (used apt to download the drivers). I thought it had worked, however the other day i installed Doomsday and tried to play Doom, and the framerate was ludicrously slow. So, i checked using fglrxinfo, and lo and behold the drivers weren't actually loaded. So, i tried uninstalling them through synaptic and reinstalling them the same way, but yet again no luck. Then i tried uninstalling them again, and tried the longer method as described on the site above. The proccess seemed to go smoothly, but yet again i restarted and the drivers hadn't loaded. So i uninstalled these, and tried again using method one (with a few little things changed) and yet again no success. The information i get from fglrxinfo is:

fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

Attached is my /etc/X11/Xorg.conf

One part of var/log/Xorg.0.log reads:

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

Is this what is causing the fault? I don't know a great deal about linux, and so any information would be much appreciated. Thanks.

---

### Post by FlamingBee on 2007-04-18
Hmm, well, after thinking "oh well, may as well give it one more shot the long way round to make sure the kernel headers were installed properly" i've somehow managed to get it to work. I think i had failed to blacklist the old driver properly, and/or hadn't followed the kernel header steps correctly. Whatever the reason, it is working now. Huzzah!

---

### Post by Fenix-TX on 2007-04-18
I have the same problem, how did you resolve it?

---

