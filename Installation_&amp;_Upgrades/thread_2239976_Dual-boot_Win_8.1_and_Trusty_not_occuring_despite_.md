---
title: "Dual-boot Win 8.1 and Trusty not occuring despite attempts to fix"
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by angel17 on 2014-08-17
Hello, 
I attempted to get a dual boot working for Win 8.1 and Ubuntu 14.04 by following the contents of this guide [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html).
After attempting the fixes to get dual boot working provided, I can only boot to Ubuntu through having the USB drive in. Is there any other ways to help resolve this? 

Thanks! :)

Note-Fixes attempted were using boot-repair and bcdedit in Admin Command Prompt.

---

### Post by ubfan1 on 2014-08-17
You might be able to fix things by running sudo update-grub  next time you are running Ubuntu.  If that doesn't fix things, take a look at the grub command next time you boot without the USB, type "e" to edit the command, and you will see part of the grub.cfg file which boots ubuntu.  Now check the devices, sometimes they are off by one (confusion caused by install media being counted when the grub.cfg file was generated).  Change the hd1 to hd0 (and any sdb to sda) and then F10 to boot.  If that works, now run sudo update-grub without the USB, and the fixes should be right.

---

