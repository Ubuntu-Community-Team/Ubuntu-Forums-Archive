---
title: "Please, help !"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by selen on 2010-07-08
**Please could someone help me ? I have already for a one week all of this is written on my screen , what should I do ? **
 
**Boot from (hd0,0)ext3c79581de-ca61-4c8c-99f7-2a357b7ab895**
**Starting up...**
**Loading,please wait...**
**Gave up waiting for root device. Common problems:**
**-Boot args(cat/proc/cmdline)**
**-Check rootdelay=(did the system wait long enought ?)**
**-Check root=(did the system wait the right device?)**
**-Missing modules (cat/proc/modules;ls/dev)**
**Alert!/dev/disk/by-uuid/c79581de-ca61-4c8c-99f7-2a35b7ab895 does not exist. Dropping to a shell !**
**BusyBox v1.10.2(Ubuntu 1:1.10.2-ubuntu7) built-in shell(ash)**
**Enter 'help' for a list of built-in commands.**
**(initramfs)**

---

### Post by selen on 2010-07-08
**Please could someone help me ?  I have already for a one week all of this is written on my screen , what should I do ? **
 
**Boot from (hd0,0)ext3c79581de-ca61-4c8c-99f7-2a357b7ab895**
**Starting up...**
**Loading,please wait...**
**Gave up waiting for root device. Common problems:**
**-Boot args(cat/proc/cmdline)**
**-Check rootdelay=(did the system wait long enought ?)**
**-Check root=(did the system wait the right device?)**
**-Missing modules (cat/proc/modules;ls/dev)**
**Alert!/dev/disk/by-uuid/c79581de-ca61-4c8c-99f7-2a35b7ab895 does not exist. Dropping to a shell !**
**BusyBox v1.10.2(Ubuntu 1:1.10.2-ubuntu7) built-in shell(ash)**
**Enter 'help' for a list of built-in commands.**
**(initramfs)**

---

### Post by philinux on 2010-07-08
You need to run ```
sudo blkid
```

And compare that with you fstab to correct the uuid's being used by fstab.

```
cat /etc/fstab
```

And correct any errors in fstab accordingly.

You can do this from the livecd with ```
gksu gedit /etc/fstab
```

Or from the shell with ```
sudo nano /etc/fstab
```

---

### Post by karthike on 2010-07-08
i also had same problem. In my case it happened because of the recent addition of a old hardware(i added my old IDE harddisk to my computer). did u install any hardware recently ?.
to continue using your linux.. wait for till the "BusyBox v1.10.2(Ubuntu 1:1.10.2-ubuntu7) built-in shell(ash)" prompt.. press CTRL+C many times till it continues with the loading of files/services.. i didnt find any solutions.

---

### Post by davidmohammed on 2010-07-08
try [this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") link - towards the bottom there is "Reinstalling from LiveCD" - try that method.

---

### Post by Elfy on 2010-07-08
Merged threads  - please do not start duplicates.

---

