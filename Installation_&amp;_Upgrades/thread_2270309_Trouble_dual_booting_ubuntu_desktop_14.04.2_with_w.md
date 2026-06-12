---
title: "Trouble dual booting ubuntu desktop 14.04.2 with windows 8.1 on ideapad z570"
date: 2015-03-22
forum: Installation &amp; Upgrades
---

### Post by ncko10 on 2015-03-22
Neither me nor my brother (who has installed linux multiple times on another device) can figure out how to install on my lenovo laptop. I've tried installing on both a burnt disc and a bootable USB created with pen drive linux. With the disc, I have tried navigating to the boot menu from the BIOS menu by pressing f2 at startup and selecting the burnt CD and I get an error message on a black screen and need to restart again. With the USB, when I navigate to the boot menu and select the USB, I just get a black screen with no error message and am required to restart again.

Following the install guide, I have discovered that the problem is most likely that my PC is too old to access the UEFI settings so I can't disable secure boot. That's why I attempted doing it from the BIOS menu by pressing f2 at startup.

This is the guide I was following: [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
I got up to step 5 before I hit my road block.

Is there an alternate way to install without needing to access the UEFI settings or can I get into those settings in another way?

---

### Post by carl4926 on 2015-03-22
One thing to remember is you need to turn off fast boot and change the settings in windows 8 relating to shutdown, because by default windows doesn't shutdown properly and this is a problem.
There is a way to boot cd or usb from within windows 8 uefi settings
But all machines I have seen seem to be different
If you plan to keep windows then you will need to install in uefi mode

---

### Post by oldfred on 2015-03-23
Do not know how similar your 570 is to a z580?

 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)

      
 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
[http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212](http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212)

---

