---
title: "Having conflict in installing graphic driver in Ubuntu 15.10"
date: 2016-02-18
forum: Installation &amp; Upgrades
---

### Post by Tegg_Sung on 2016-02-18
Recently, I installed Ubuntu 15.10 in my desktop. Now I am having trouble in installing nVidia graphic driver. Tried various methods in different blogs, I almost gave up. 

My desktop environment:
	Intel i7 6600 Skylake
	MSI Z170 krait gaming 
	GeForce 970
	Sandisk 256GB SSD
	
I bought the most up-to-date hardware. Installed Ubuntu in UEFI mode and 15.10 and 16.04 version (14.04 and 15.04 even cannot load installation after GRUB menu -- I don't want to use nomodeset method)

I could detected graphic hardware using
	lspci -k | grep -EA2 'VGA|3D'
At first kernel driver is nouveau. Followed step by step and after rebooted, black screen just looped (I think this is called 'kernel panic')

With 'control + alt + f1' and entered verifying graphic command, I could found kernel graphic is changed to nvidia, but because of kernel panic, I have to purge nvidia. 

I tried nvidia version 352, 355, 358, and 361. But same results have shown. I think, this is because my hardware is so new that software hasn't updated yet. 

Does anyone get same problem as mine?

---

### Post by echotech2 on 2016-02-18
Needs a bit of clarification.  Were these drivers loaded from "Additional Drivers"? It doesn't sound like it.

---

### Post by grahammechanical on 2016-02-18
The newest hardware requires the newest Linux kernels and driver modules that come with them. That is why you need the newest versions of Ubuntu. But even then the Linux developers are behind because the manufacturers do not cooperate for commercial reasons.

If you have succeeded in installing Ubuntu and can load to a working desktop, then you can go to System Settings>Software & Updates>Additional Drivers tab and let that utility find some proprietary (Nvidia) drivers and install them for you. That is really the best way of doing things. Additional Drivers will only offer us proprietary video drivers that support our hardware.

As an example, I am running 16.04 which I find stable enough for daily use. Additional Drivers does not offer me a Nvidia driver newer than 340 because the newer video drivers have dropped support for my old video adapter. Installing a video driver that is too old for our newest hardware will of course cause problems.

Edit: The Nvidia web site says that the Geforce 970 is supported by Nvidia 352; 355; 358 & 361 driver versions.  And I think that Additional Drivers in Ubuntu 15.10 will offer 352, 355, 358 if not 361. So, I am not sure why you are having this problem.

Regards.

---

### Post by Tegg_Sung on 2016-02-18
I added repository and get installed by command such as "nvidia-352" and so on. Also I tried to installed using "additional driver" that is proprietary and binary driver.

However, the result is same. Kernel driver is shown as nvidia, but the log-in screen does not appeared.

After typing "uname -r", 4.2.0 generic version is found. 

Does it because the compatibility of nvidia hardware and MSI mainboard, or with Ubuntu is bad?

---

