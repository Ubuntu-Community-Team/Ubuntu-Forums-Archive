---
title: "Kernel Linux 3.2.0-49 generic pae"
date: 2013-07-10
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2013-07-10
I just noticed that this old laptop (mobile AMD Athlon XP2400+, 512 megs of RAM) which is having some minor problems running 12.04 LTS, is using a PAE enabled kernel. Could this be the cause of my woes? (will not complete shutdown, I have to switch off the power supply). Is it possible to re-install a non PAE kernel more appropriate for the processor? does it matter any? 

Laptop works correctly 95% except for shutdown.

According to this thread: 
[http://askubuntu.com/questions/19389/whats-the-meaning-of-pae-at-the-end-of-kernel-version](http://askubuntu.com/questions/19389/whats-the-meaning-of-pae-at-the-end-of-kernel-version)
first answer, there might be a connection.

Thanks for ur help.

---

### Post by dino99 on 2013-07-11
pae can use more than 3 giga; but also works with less indeed.
your shutdown issue is due to something else (maybe some oldish settings from the hidden folders (.local, .gconf, .gnome2, .config)), try to rename them and reboot to get fresh new ones.

---

### Post by mayagrafix on 2013-07-11
Its a new install, including a complete HDD erase and new partitioning. I have installed no other software other than the recomended auto updates and a couple of PDF files. Are u sure that updating the kernel is not warranted?

---

