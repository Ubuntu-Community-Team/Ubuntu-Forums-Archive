---
title: "Target File System  doesn't have /sbin/init"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by xerionn on 2007-11-12
So i did a clean install of 7.10 from the alternate cd cause this is the way i prefer it.

Installation went fine however after the system restarts i get the message :

mount: mounting /dev/root on /root failed: no such file or directory
Beign: Running /scripts/local-bottom
Done.
Done.
Beign: Running /scripts/init-bottom
mount: mounting /root/dev on /dev/ .static/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v.1.1.3 ...etc


Any idea ?

---

### Post by solar george on 2007-11-13
In the grub menu edit the boot entry to use a /dev/xyz root (the correct one obviously) rather than using UUID

---

### Post by xerionn on 2007-11-13
I dont use Grub cause i use Lilo since before the installation of ubuntu
I have already installed Slackware Gentoo and Win XP in the laptop and said lets try ubuntu ... 

I just added ubuntu to the lilo.conf and was using /dev/sda6 where sda6 is the partition i have for ubuntu

Any idea ?

---

### Post by solar george on 2007-11-14
Did you remember to use the initrd?

---

### Post by xerionn on 2007-11-14
Yus i had it set but i logged to slackware and saw that i had set root = /dev/sda5 and well the correct one was sda6 as i had posted here :P

Duh *bonks head silly me :/ sorry

Thank you you for your time and the answers

---

