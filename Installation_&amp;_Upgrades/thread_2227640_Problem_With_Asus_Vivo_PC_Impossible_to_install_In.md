---
title: "Problem With Asus Vivo PC Impossible to install Install Ubuntu 14.04 32bit or 64bit"
date: 2014-06-03
forum: Installation &amp; Upgrades
---

### Post by minus2 on 2014-06-03
Hello
Impossible To Install Ubuntu 14.04 64bits on my pc Asus VivoPC VC60 (View picture)
I tried to install Ubuntu 14.04 32bits but after update i have a black screen
Help me help me ?
Thinks
[IMG]http://cdn.imghack.se/images/3fd278653c9cc8c2ec6ac52378d2814c.jpg[/IMG]

---

### Post by oldfred on 2014-06-05
If you have Windows 8 in  UEFI boot mode only the 64 bit version of Ubuntu includes UEFI.

Is this a system that is locked? Most are not, but a few are. 

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

      
 Bay Trail -The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)

Some other models of Asus, UEFI may be similar.

  Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
ASUS Zenbook UX301LAA ultrabook under Linux  - reboot, power issues
[http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ)
 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

---

### Post by ubfan1 on 2014-06-05
You also might turn off wireless until you have installed, then turn it on, and if problems, use an ethernet cable to download a proprietary driver if necessary.  Your kernel crash looks like the wireless driver had a problem.

---

### Post by zeno3 on 2014-09-03
> **minus2 said:**
> Hello
Impossible To Install Ubuntu 14.04 64bits on my pc Asus VivoPC VC60 (View picture)
I tried to install Ubuntu 14.04 32bits but after update i have a black screen
Help me help me ?
Thinks


Hello minus2,
I had the same problem with my Asus VivoPc VM40B, using the same wlan chipset (realtek 8821).
I solved the issue in the following way:
1) install Ubuntu 14.04 64bits with the wireless lan **disabled **from BIOS (or UEFI).
2) upgrade of the linux kernel from 3.13 to **v3.15-rc2-trusty**.

After rebooting the wlan was visible (lshw) and up.:D

Hope this helps, and if you need details, just ask.
Ciao
Zeno

---

