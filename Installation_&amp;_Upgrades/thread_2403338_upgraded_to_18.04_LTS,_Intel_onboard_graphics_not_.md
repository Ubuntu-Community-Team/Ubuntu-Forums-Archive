---
title: "upgraded to 18.04 LTS, Intel onboard graphics not working anymore"
date: 2018-10-10
forum: Installation &amp; Upgrades
---

### Post by gr0nd on 2018-10-10
This problem has been discussed before, marked "SOLVED" with the solution being "use another distro". I don't think that this is a solution at all. So here we go again:  After upgrading to 18.04 LTS from 16.04 the graphics system freezes after boot. Giving GRUB the "nomode" option results in a working system, however, the boot progress dots that cycle through white and orange during boot are still present on the desktop after login which is pretty annoying. So I added the GRUB option "nosplash" and I get a usable system. The problem now is that the maximum resolution available is limited to 1600x1200 (through the corresponding GRUB option) and my screen is 1920x1200. All this because apparently the intel graphics drivers in 18.04 LTS do not work for older onboard graphics chipsets. I don't need much graphics power but I at least want to run a proper screen resolution. I tried the different acceleration options in xorg.conf but they didn't make any difference. Is there any hope?   ```
 # lspci|grep  VGA 00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)    # apt list|grep intel|grep xorg    WARNING: apt does not have a stable CLI interface. Use with caution in scripts.    xserver-xorg-video-intel/bionic,now 2:2.99.917+git20171229-1 amd64  [installiert]  xserver-xorg-video-intel-dbg/bionic 2:2.99.917+git20171229-1 amd64  xserver-xorg-video-intel-hwe-16.04/bionic 3:14.1 amd64  xserver-xorg-video-intel-hwe-16.04-dbg/bionic 3:14.1 amd64  xserver-xorg-video-intel-lts-vivid/now 2:2.99.917-1~exp1ubuntu2.2~trusty1 amd64 [Konfiguration-verbleibend] 
```

---

### Post by gr0nd on 2018-10-10
Um, okay, so how do I get newlines in my forum posts?

---

### Post by Claus7 on 2018-10-11
Hello,

> **gr0nd said:**
>  

```
 # lspci|grep  VGA 
00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)    
# apt list|grep intel|grep xorg    
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.    
xserver-xorg-video-intel/bionic,now 2:2.99.917+git20171229-1 amd64  [installiert]  
xserver-xorg-video-intel-dbg/bionic 2:2.99.917+git20171229-1 amd64  
xserver-xorg-video-intel-hwe-16.04/bionic 3:14.1 amd64  
xserver-xorg-video-intel-hwe-16.04-dbg/bionic 3:14.1 amd64  
xserver-xorg-video-intel-lts-vivid/now 2:2.99.917-1~exp1ubuntu2.2~trusty1 amd64 [Konfiguration-verbleibend] 
```

-the format was fixed by pressing enter-

The last line has to do with ubuntu trusty and ubuntu vivid. Under my system (with similar output), that line does not exist. I would advice you to remove that package and see if it avoids any conflicts, yet try with caution.  

Regards!

---

