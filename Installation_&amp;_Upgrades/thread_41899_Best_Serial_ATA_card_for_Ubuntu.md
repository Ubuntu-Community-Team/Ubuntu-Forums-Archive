---
title: "Best Serial ATA card for Ubuntu?"
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by geokker on 2005-06-15
I have used Ubuntu for a while on my laptop and find it to be simpler and faster than Windows XP. I have tried to install it on my Dell desktop but have run into problems.

I have two sata disks plugged into a controller - itself plugged into a PCI slot.

The sata controller is a software jobbie, and the company seems not to want to produce adequate Linux drivers, so effectively turning my vanilla Dell into a Windows-only machine.

When I get to the partitioning point in the installation procedure, the individual disks are detected correctly i.e. model & size. When I try to partition them or create a software RAID array, many different errors occur - I've tried virtually every permutation.

I have concluded that the card is simply not Linux compatible. I've scurried back to an IDE drive.

So now I have two redundant (no pun intended) sata drives and PCI controller card. Rather than chuck the drives in the bin, which sata controller can I buy that is Ubuntu compatible?

Machine details:

PIII 1GHz Dell Optiplex GX150 tower
SiL 3114 (Silicon Image formerly CMD) sata RAID (software) controller
80GB Maxtor
120GB Western Digital
Hoary 5.04 Ubuntu

---

### Post by norman_h on 2005-07-05
You could always attempt software RAID...

If you want the easy way out, then a RocketRAID1540 card by highpoint should work.

---

### Post by geokker on 2005-07-06
I've looked at RocketRAID 1520 and it seems to be ideal - I only have the fans for 2 disks. Do I need to install the drivers? Does it definitely work with Ubuntu? How much grief can I expect?

If I buy it, I'll be sure to post a much needed how-to.

Also, will it noticibly increase performance on a P3 Hoary Dell?

---

### Post by norman_h on 2005-07-06
My 1540 card uses the HighPoint HPT374 chipset.  The chipset is the most important thing when determining if the card will work.  It appears that the 1520 card is supported under linux.  There is support in the kernel for the following HPT chipsets:
HPT366
HPT368
HPT370
HPT372
HPT374

I don't use the card on my ubuntu machine and I don't have a module as I compiled it directly into my kernel of its host machine (its an LFS build), however, I think the module name is hpt366  It appears (from a quick modprobe of my ubuntu 5.04 box) that the module is already compiled for ubuntu and it will probably get picked up at boot time.  I don't know how easy it will be to get your system to boot from the card as I have never tried it and I only use my 1540 card as a mass storage device and the system that hosts it has its main root partition on an IDE disk.  It appears that the card will be picked up at boot time in ubuntu.  The devices that my RAID box picked up are /dev/hde /dev/hdg /dev/hdi /dev/hdk  you could expect something similar.

> Also, will it noticibly increase performance on a P3 Hoary Dell?
Compared to what?  If you stripe the drives into RAID0 you may notice a difference in initial application startup and system boot times, but the main determination of speed IMHO is RAM.

---

### Post by geokker on 2005-07-06
I'm in a tricky situation now. I'm curious to try the card out. I definitely had a performance gain with Windows XP and RAID0. I've got Ubuntu on an old-ish 80GB IDE running fine now. I agree that RAM is the man. With the RAID in, the bottle neck might be my P3 chip. 

Decision made. Considering the age of my machine and the fact that it runs fine for my purposes, I'll give it a miss. When I upgrade the motherboard, I'll look at the state of affairs. This could be 2 years away. Maybe I'll buy another 512MB RAM...

---

### Post by norman_h on 2005-07-06
I'm only running 512Meg RAM in my AMD3000+ box and while the RAM does eventually get filled up, I find that 512 is more than enough for ubuntu/firefox/openoffice/email/xmms/gftp/xchat all at the same time.  While I'm not useing RAID0 at the moment, I have played with it before and there is a performance increase, but this is only when loading apps from the hard disk.  Once the apps are in the RAM the RAID0 make no difference unless you run out of RAM and start using swap space on you hard disk.

Best of luck!

---

