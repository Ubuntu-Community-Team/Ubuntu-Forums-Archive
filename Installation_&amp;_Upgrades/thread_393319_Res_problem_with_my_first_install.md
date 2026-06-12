---
title: "Res problem with my first install"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by Yaka on 2007-03-25
i am a newbie just installed ubuntu last night on my nforce2 based shuttle XPC SN41G2. i am using the onboard gfx and sound but my res is stuck  at 800x600 i am connect to my LG lcd tv over vga an am wanting a res of 1366x768 anyone wana help me please 

thanks in advnace for any help

---

### Post by bulldog on 2007-03-25
First of all,which ubuntu do you have?

Installing the driver for your graphics should be correcting things.
After the driver install perform```
sudo dpkg-reconfigure xserver-xorg
``` and choose the desired resolution.
Your graphics must be able to let you use this resolution.

---

### Post by Yaka on 2007-03-25
hi mate, the ubuntu i have is the latest 6.10 desktop install from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) i thinks its edgy but not 100% sure

and i shall just try that now thanks

---

### Post by bulldog on 2007-03-25
Edgy is 6.10,and to install the graphics driver take a look here,
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

