---
title: "Installation Problem"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by lionking212 on 2007-12-29
Hey Guys, I'm trying to install Ubuntu version 7.10 from a live CD but i keep running into a problem. After loading the menu, I hit install and it starts loading all the drivers and then the screen turns blank and after sometime even the cd stops spinning. It happens to all the options. Is it a problem with my laptop or would the problem be solved by downloading a different iso file? Please help me guys. My config is P4 2.66 768MB RAM 32MB ATI radeon 7500. Thank you

---

### Post by bharadwaj on 2007-12-29
may be the drivers of you laptop have not been included in the live CD. Installing Ubuntu with an alternated CD would fix the problem 100%

---

### Post by chevylvr on 2008-01-14
I have used the alternate installation cd and the screen is blank after choosing which OS to boot or just 7.10 installed clean on the system. If I choose the "Recovery" option and startx it will load GDM fine and function properly. I checked the xorg.conf and it is using the generic driver (VESA)

Dell Inspiron 5100 ATI mobility 7500 32 MB 2.4 Ghz. PCLinux 2007 is fine on the system and that it was it is running currently. Ubuntu is not installed so no way to get the contents of the xorg.conf file (wife's system and needs to work :D )

---

### Post by chevylvr on 2008-04-02
I used the alternate installation cd and it still failed. I found another post in the forums:
[http://ubuntuforums.org/showthread.php?t=580134&highlight=inspiron+5100+troubleshooting](http://ubuntuforums.org/showthread.php?t=580134&highlight=inspiron+5100+troubleshooting)

and added this line to the /etc/X11/xorg.conf under the display adapter line:
Option "LVDSBiosNativeMode" "FALSE"

and all started fine and compiz worked fine.

---

