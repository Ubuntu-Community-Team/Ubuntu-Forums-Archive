---
title: "Old monitor"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by Steelegbr on 2006-07-13
Hi,

I have downloaded the 6.06 live CD for my computer system (detailed below). After selecting the first option on the boot menu, the boot process completes but produces garbled output (resolution and/or resfresh rate too high for monitor).

I have tried to force the resolution down (F4) but with no success.

Is there any way of editing the boot: string to force a lower resolution?

Steelegbr

AMD Athlon 1600MHz
256Mb Ram
20Gb HDD
NVidia GeForce 4 64Mb (AGP)
DVD-RW & CD-RW (Both bootable)
Packard Bell Monitor (Max 800x600 resolution).

---

### Post by orb9220 on 2006-07-13
Can tiy get to terminal prompt to type this?

sudo nano /etc/X11/xorg.conf

Then scroll down and modify the section monitor and section device.
Look for Horz. refresh and check to see it is should read 30-50 hz and vertical should be 60.

Also look at screen resolution and delete ex: "1024x768" or 1280x1024" etc.  May be in more than one place.

Are you using defualt ubuntu drivers or have you installed any nvidia drivers?

If you look in device you should see under monitor also "nv" for driver or 
"nvidia" for there driver which you don't need for older.

But if your's says "nv" then it should work just check res and horz and vert refresh.

also do forum search on: geforce 4 and see what popups

---

### Post by Steelegbr on 2006-07-14
I downloaded the text-based installer.

Problem solved.

---

