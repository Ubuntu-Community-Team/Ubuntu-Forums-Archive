---
title: "Need help installing 8.04 on MSI GX620"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by quantumrand on 2008-10-01
I just got a new MSI GX620, but I'm having issues installing 64bit 8.04. I've installed Ubuntu on several systems in the past, but never ran into this issue before.

When I try to either install or boot the live CD, it hangs at BusyBox. My guess is that Ubuntu doesnt like my AHCI, but when I change the setting to RAID, my system cant find my DVD-Drive.

Here's my system specs if that'll help:

CPU: Core 2 Duo P8600
GPU: nVidia 9600M GT
RAM: 4GB DDR2-800
HDD: 320GB Sata
Chipset: PM45 + ICH9-M

Does anyone have any ideas?

---

### Post by brewster1486 on 2009-02-25
Just got a new GX620 (GX620-038US) a few days ago. 8.10 Live CD booted up like a charm. EVERYTHING worked "out of the box" - wireless fine, e-sata fine, graphics great, built-in webcam works (ekiga and skype both recognized it), volume buttons work..

---

### Post by brewster1486 on 2009-02-28
Just installed Jaunty 9.04 Alpha 5 and it works perfectly.

---

### Post by wanged on 2009-06-13
Perfectly, like even the turbo and eco modes work?

---

### Post by plr4ever on 2009-06-20
I just installed 9.04 x64 and it works near perfectly, with a couple of exceptions:

My bluetooth module doesn't work out of the box, and i am in the process of searching for drivers. i'll post them if i can find them Does anyone know the exact bluetooth module model number? or is it part of the centrino chipset?

Also, the turbo and eco buttons will not work in linux, at least without modification. they work in windows with a program called system control manager that is provided by MSi. they won't work because this program doesn't have a linux version. the buttons do not physically overclock it directly, they just instruct the program to do so. 

Other than that, i have had no issues so far. This is a wonderful laptop, and was one of the easiest to install, driver wise.

[EDIT]
I was mistaken, the bluetooth does actually work, although i am having a tough time getting it to connect with my Microsoft Bluetooth Mouse O.o

---

