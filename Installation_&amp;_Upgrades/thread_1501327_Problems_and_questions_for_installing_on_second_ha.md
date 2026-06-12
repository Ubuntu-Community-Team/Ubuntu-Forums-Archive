---
title: "Problems and questions for installing on second hard disk"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by dtkr on 2010-06-04
I have two hard disks on my machine. Each disk is split into two partitions. The first disk, /dev/sda, has Windows XP installed on the first partition and data on the second. The second disk, /dev/sdab has its first partition empty and the second filled with data. All partitions are NTFS.

I installed Ubuntu 10.04 on the first partition of /dev/sdab and rebooted. When setting the BIOS to boot from the disk containing XP, I get a blank screen with a blinking cursor after the BIOS hands control to the system. When setting the BIOS to boot from the second disk (the one with Ubuntu installed), I get a request to insert "media" and press any key to continue.

Any ideas on why this occurred and how I can set up my system properly? I know that this has something to do with the MBR and GRUB being installed somewhere... ...

Thanks for the help (in advance:))

---

### Post by dtkr on 2010-06-04
Oh Yeah, I heard that it is now impossible to choose where you want to install GRUB in the default installation. Which means that I installed to the MBR of the first disk and hence screwed up the system.

---

### Post by hansdown on 2010-06-04
Hi dtkr.

You can still choose where to install grub.

Herman has a really good tutorial.

[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by kansasnoob on 2010-06-04
If you require detailed help please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dtkr on 2010-07-08
Thanks for your help. Problem Solved.

---

