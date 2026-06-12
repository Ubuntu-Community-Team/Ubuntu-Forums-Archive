---
title: "Installation problem."
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by [Johnny] on 2007-10-10
After downloading Ubuntu i burnt it to the cd like in the tutorial, it reads it all fine when on windows and it looks like the example of how the CD is supposed to look.

When i boot my computer with the CD drive prioritized it begins to read the disk, but does not load an installer. It proceeds to load my windows xp version. (im erasing winxp and putting ununtu on it). All im wondering is why the disk is not loading an installer... everything was done by the guide and its correct. I didn't do the priorities wrong because ive rebooted windows for people countless times who get the "blue screen of death" or a boot error and i know how to set CD drive as priority in BIOS... help :(

---

### Post by Pumalite on 2007-10-10
Post specs. Try Alternate CD

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by [Johnny] on 2007-10-10
> **Pumalite said:**
> Post specs. Try Alternate CD

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

OS Name	Microsoft Windows XP Home Edition	
Version	5.1.2600 Service Pack 2 Build 2600	
OS Manufacturer	Microsoft Corporation	
System Manufacturer	INTEL_	
System Type	X86-based PC	
Processor	x86 Family 15 Model 3 Stepping 4 Pentium 4 ~3400 Mhz	
Windows Directory	C:\WINDOWS	
System Directory	C:\WINDOWS\system32	
Boot Device	\Device\HarddiskVolume1	
User Name	JOHN\John	
Time Zone	Eastern Daylight Time	
Total Physical Memory	1.00 GB	
Available Physical Memory	580.91 MB	
Total Virtual Memory	2.00 GB	
Available Virtual Memory	1.96 GB	
Page File Space	1.15 GB

---

### Post by Pumalite on 2007-10-10
Graphics?

---

### Post by [Johnny] on 2007-10-10
> **Pumalite said:**
> Graphics?

That wouldn't have anything to do with why it isn't booting from the disc..... but i got a GFX GeForce 8800 ULTRA with 768MB memory on it...

---

### Post by Pumalite on 2007-10-10
Well, your card is pretty new. What version of Ubuntu are you installing?.

---

### Post by [Johnny] on 2007-10-10
> **Pumalite said:**
> Well, your card is pretty new. What version of Ubuntu are you installing?.

the one on downloads page, 7.0.4 release for x86 pcs (what pentium is)... and yes i made sure its desktop edition :P

---

### Post by nzadLithium on 2007-10-10
You will need to use the alternate cd to install ubuntu. I don't think Ubuntu feisty comes with graphics drivers which will work with your card because when feisty was released the nvidia drivers would not have been recent enough to support your card. You will need to install the latest nvidia drivers to get your xserver up which is why you must use the alternative text based installer.

However like you said it should not still be booting windows. I would expect the ubuntu loading screen to finish and then you receive an xserver error.

what tutorial did you follow to burn the cd? It seems like your cd is not a bootable cd for some reason which makes me think there may have been something you missed in the tutorial or the tutorial is incorrect. The instructions Pumalite posted a link to should work. Just make sure you use the alternate cd.

---

