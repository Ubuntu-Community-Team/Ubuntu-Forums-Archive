---
title: "can not get Ubuntu to boot with new hardware"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by mgh24 on 2011-02-16
Hello All,

I have recently built a new desktop, nothing fancy.  Installed Windows 7.

Ubuntu starts to boot, and then freezes, and I get a jumbled display, in which I can see jagged pieces of my Windows desktop.

This happens when I try to boot from CD, or if I install via wubi, and try to boot from hard drive.

The CD will boot on my laptop.

Any ideas how I can get a successful boot on the new desktop?

Thanks for any suggestions.

---

### Post by ajgreeny on 2011-02-16
> I have recently built a new desktop, nothing fancy.  Installed Windows 7.
That's not very useful information to help us solve anything.   Did Windows 7 work OK?

What is "nothing fancy" please, as it tells us absolutely nothing about your hardware.  So please tell in more detail what you have put together, particularly the graphics card, which I think is the most likely problem item.

---

### Post by mgh24 on 2011-02-16
Sorry, here are some details.

MSI 870-G45 motherboard
EVGA GeForce 240 nividia graphics card (I have not updated any drivers)
4 gig G-Skill RAM
AMD athlon II X 3 450 cpu

2 cd/dvd drives, both connected via SATA.

Have had no issues with Win 7, running a little over a month.

Thanks for the help
 
I just now updated graphics driver.  It had no effect.

---

### Post by bcbc on 2011-02-16
Boot with the nomodeset option: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by mgh24 on 2011-02-16
The nomodest worked!
  
Running on the live CD, I am unable to set monitor resolution to anything higher than 1280 X 1040.  This has me concerned, as I want 1680 X 1050.  Is this something I will be able to correct if I get Ubuntu installed?

I am a little unclear as to how to open a terminal to make this change permanent.  I will go through this same boot process after installation, selecting nomodest on boot, and then open the terminal and follow instructions?

Many thanks!

---

### Post by Quackers on 2011-02-16
The info to make the change permanent is included in the link bcbc posted.
However, if you install proprietary drivers, if available (using System > Admin > Additional Drivers) that change may not be necessary.
To open a terminal go to Accessories menu and select Terminal.

---

### Post by mgh24 on 2011-02-17
You were absolutely correct.

I had to boot in safe mode after installation, then install graphics driver, and I am up and running perfectly.

Thanks for the help.

---

