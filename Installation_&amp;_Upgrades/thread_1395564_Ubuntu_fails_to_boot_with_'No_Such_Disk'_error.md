---
title: "Ubuntu fails to boot with 'No Such Disk' error"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by UBigmac on 2010-02-01
I've installed **Ubuntu Server V9.10** (**64-bit**) on a brand new server I built with no previous OS installed.  The drives are two Hitachi  1 Tbyte hdd's configured as RAID1, an ASUS M4A78T-E motherboard with an AMD Phenom-II cpu with 8 Gbyte of memory.  I updated the bios following building the computer.   

The Ubuntu 9.10 server installation appears to go without error.  However, on reboot I get the message:

Grub loading
error: no such disk
grub rescue

I suspect the MBR is missing or Linux is not pointing to the correct drive in the grub.cfg.  

I'm a noob to Linux.  I've made sure the boot order is correct, but other than that I don't really know the commands or syntax to troubleshoot this problem.

The only CD I have is the Ubuntu 9.10 server ISO I downloaded and burned to dvd.

Any suggestions would be appreciated.

---

### Post by presence1960 on 2010-02-01
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

