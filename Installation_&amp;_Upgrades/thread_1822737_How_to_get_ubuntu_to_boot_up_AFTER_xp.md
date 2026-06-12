---
title: "How to get ubuntu to boot up AFTER xp?"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by car0003 on 2011-08-10
sorry ima noob but i recently installed ubuntu 11.04 on my desktop (duo  boot with windows xp), and when my computer boots up. i get the timer  that chooses ubuntu in like 10 seconds if i dont choose anything.

i used to have 10.04LTS on my laptop with Vista as well, only the timer chose vista if i didnt decide. So my question is:
[SIZE=3]**How do i get my desktop to choose XP instead of ubuntu?**[/SIZE]



i tried going to the boot.ini file in xp, but it assumes its the only operating system

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

so i need to know how to edit it with in ubuntu
PLEASE HELP

---

### Post by Neraste on 2011-08-11
Hello **car0003**

Windows and any Linux OS don't have the same process to boot, that is why you cannot see any other OS than Windows on your *boot.ini* file.

To perform a dual boot, Linux installs GRUB or GRUB 2 (GRand Unified Bootloader) which allows you to choose which OS to boot with; this is the timer you're speaking about. You have to configure it to switch your default OS, everything takes place on Linux.

I advise you to have a look at [the GRUB 2 documentation webpage]("https://help.ubuntu.com/community/Grub2").

---

### Post by Megaptera on 2011-08-11
Car0003,
Have you tried installing and using 'startupmanager' ? guide with screenshots here:

[http://www.howtogeek.com/65974/how-to-easily-change-your-dual-booting-pcs-default-os/](http://www.howtogeek.com/65974/how-to-easily-change-your-dual-booting-pcs-default-os/)

Quote "GRUB is pretty robust and also really daunting to configure for beginners. Luckily for us, there&#8217;s a great GUI-based tool in Ubuntu&#8217;s repositories: StartUp-Manager."

---

### Post by car0003 on 2011-08-14
> **Megaptera said:**
> Car0003,
Have you tried installing and using 'startupmanager' ? guide with screenshots here:

[http://www.howtogeek.com/65974/how-to-easily-change-your-dual-booting-pcs-default-os/](http://www.howtogeek.com/65974/how-to-easily-change-your-dual-booting-pcs-default-os/)

Quote "GRUB is pretty robust and also really daunting to configure for beginners. Luckily for us, there&#8217;s a great GUI-based tool in Ubuntu&#8217;s repositories: StartUp-Manager."

Thankx :) this is exactly what i needed. u helped me out alot :)

---

### Post by Megaptera on 2011-08-14
Glad it helped!!

---

