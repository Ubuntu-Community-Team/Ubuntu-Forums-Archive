---
title: "Installation does simply nothing"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by Sanix on 2008-09-16
I tried to install Ubuntu on my laptop. The newest version 8.04 is it I reckon. When I press the button install ubuntu, it tries to load the kernel but it does simply nothing after it reached 100%. After a while, it simply restarts the computer and nothing has happened. When I tried to install it in English, I got once the error message casper/vmlinuz, but just once. I googled and figured out, that it should only happen with flash drives. But I'm trying to install it from CD.

---

### Post by oilchangeguy on 2008-09-16
> **Sanix said:**
> I tried to install Ubuntu on my laptop. The newest version 8.04 is it I reckon. When I press the button install ubuntu, it tries to load the kernel but it does simply nothing after it reached 100%. After a while, it simply restarts the computer and nothing has happened. When I tried to install it in English, I got once the error message casper/vmlinuz, but just once. I googled and figured out, that it should only happen with flash drives. But I'm trying to install it from CD.

computer specs please.

---

### Post by Sanix on 2008-09-16
Dell Precision M60

Systemname	M60	
Systemhersteller	Dell Computer Corporation	
Systemmodell	Precision M60	
Systemtyp	X86-based PC	
Prozessor	x86 Family 6 Model 13 Stepping 6 GenuineIntel ~1993 Mhz	
	
RAM	2'048.00 MB	

Graphic card NVIDIA Quadro FX Go1000	

Harddisk
Name	Intel(R) 82801DBM Ultra ATA Storage Controller - 24CA

---

### Post by Sanix on 2008-09-16
I tried it with the parameter aic7xxx.aic7xxx=no_probe , which should help for some DELL systems. The error differs sometimes now and says someting like casper/initgz or similar

---

### Post by dkann on 2008-09-16
Worse yet.  I'm trying to install 8.04 on a Dell Optiplex 755 and the installation program reverts to text instead of GUI.  Is there an incompatibility with Linux in general or Ubuntu specifically that I should know about?  Is there a fix?

---

### Post by Sanix on 2008-09-18
I found out, that it might be the CD Rom drive, which is extremely picky in regards of installing Ubuntu. I used an USB stick to install and it worked now. It might be, that Ubuntu doesn't really support Dell laptop CD drives.

---

