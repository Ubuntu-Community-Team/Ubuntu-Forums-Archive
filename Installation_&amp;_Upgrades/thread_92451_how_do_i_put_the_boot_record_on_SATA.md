---
title: "how do i put the boot record on SATA ??"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by jamesford on 2005-11-19
i have a problem, i dont know how to put the boot record or boot partition or what its called on the physical harddisk of my choice

i want it on one of my SATA disks (on the disk with / ) but the installer puts it on one of my IDE disks. i thought maybe the arrow/lightning icon (see screenshot) indicated that this was the boot drive but no, i had to change the boot device in bios to the first IDE to be able to boot. the only way ive found to force the boot stuff on the sata is to unplug the other drives during install.

how do i do it doing install, how do i specify where the boot stuff goes ?


[http://img295.imageshack.us/img295/3547/000011xg.jpg](http://img295.imageshack.us/img295/3547/000011xg.jpg)

---

### Post by yesplease on 2005-11-19
Edit: I gave the answer to another question. Thats not usefull :)

---

### Post by RSX311 on 2005-11-26
I had the exact same problem.  I ended up physically unplugging the power to the IDE hard drive and let ubuntu only see the SATA drive I want grub to be installed on.  Then I plugged the power back in after installation was done. Pain the in the ass I know, but it works.

---

### Post by Dogers on 2005-11-27
I've had this problem too - I normally unplug the IDE drives, so the SATA drive is seen as the first one, although I discovered recently that if you say NO to putting it on the MBR, it asks where you want it. You *MIGHT* be able to say /dev/sda (or whichever) here and have it work, but I've not managed to test it yet due to some other issues I've had..

---

### Post by bwog on 2005-11-28
When grub  is not on the partition you want after installation of ubuntu, you can use the method in: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)

To put Grub on sata disk a, you would use /dev/sda (instead of /dev/hda), to put grub on floppy diskette you use /dev/fd0. 

So you can put grub anywhere you want, but it is only usefull to put it in a place where the system can boot from, e.g. with grub on floppy you need to tell the bios to boot from floppy.

Like Dogers mentioned, you can put grub where you want during installation: at the question 'Put grub on the mbr' you answer No, and will get a menu where you can say where grub has to go. However, when you are new to ubuntu, just let it put grub on the mbr, and change afterwards, if necessary.

---

