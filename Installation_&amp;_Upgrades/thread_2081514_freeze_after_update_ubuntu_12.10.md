---
title: "freeze after update ubuntu 12.10"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by frans1t1 on 2012-11-07
Why does my laptop hang after update & upgrade ubuntu 64bit 12:10

on Asus X401U:
Processor: AMD ® &#8203;&#8203;Brazos APU Processor
Chipset: AMD A68M
Memory: DDR3 MHz SDRAM, 2 GB
Display: 14.0 "16:9 HD (1366x768 ) LED Backlight
Graphics: AMD Radeon ® HD 6290
Storage: 320GB
Card Reader: 2-in-1 card reader (SD / MMC)
Webcam: 0.3 Mega Pixel Fixed web camera
Networking: Integrated 802.11 b / g / n

help me, how to resolve this case, I have installed 7 times and the results remain the same

---

### Post by UltimateCat on 2012-11-07
Hi:

```
Why does my laptop hang after update & upgrade ubuntu 64bit 12:10

```

Not sure why but hardware failure is a possibility.
To test your system I suggest running Memtest 86; it's a good diagnostic tool-
[http://www.memtest.org/](http://www.memtest.org/)

Also, there is the chance that your
```
 AMD Radeon ® HD 6290 Card may need a driver

```
A driver installed for your Radeon card may help-
To find out which Radeon card you have run the command " lspci" in a terminal and read carefully thru the output to find your card # Than visit the Radeon website. 
[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)

Hope this helps

---

### Post by frans1t1 on 2012-11-07
I've installed via [http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)
but it does not work, error.

and if the laptop was shut down and then turn it back on then emerge grub menu after select the laptop freeze when any
load initial ramdisk
_

but if the install ubuntu 12:04 there was no trouble.

---

### Post by UltimateCat on 2012-11-07
Sounds like it could be hardware failure.

Is your laptop an older computer?

If I were you I would:

- Do a fresh install of Ubuntu but not 10.04- (pretty sure it's not supported)
- Run Memtest 86 and go through the output to see if any of the hardware is   failing.

Other than that; frans1t1:
The only other thing I can think of is that you purhaps made an error while allocating GB's to the 2 partition's (journaling file system / and the swap) that you created during the install.

---

### Post by frans1t1 on 2012-11-07
this not old computer, 
[http://id.asus.com/Notebooks/Versatile_Performance/X401U/#specifications](http://id.asus.com/Notebooks/Versatile_Performance/X401U/#specifications)

maybe could be hardware failure.

---

### Post by UltimateCat on 2012-11-07
Yeah, hardware failure or your installation didn't get configured correctly

When I installed my distro I specifically allocated 20GB for the journaling file system (/) and 1 GB for the swap but I went into manual mode and expert mode when I manipulated the partitions because I'm in a dual boot with Win's XP.

If you end up re-installing take your time with the installer and the partition manager one mistype can make a real mess-

If it is hardware failure you can take your computer to shop or a computer tech and they can make a diagnoses.

Good luck to you

---

### Post by frans1t1 on 2012-11-07
Thank you, maybe I'll study harder. and end with surrender for success

---

