---
title: "Need help install freezes"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by deathbyswiftwind on 2008-11-27
Okay I have a problem. When I try to install ubuntu 8.10 on my new computer it gets right past the partitioning and then my cdrom stops responding. It just dies like its not getting any power I cant even eject the cd and none of the cdroms lights are on. Ive tried installing multiple times with multiple copies of the ubuntu cd in both versions of the install cd (alternative and graphical). 

Im really not a fan of vista so if anyone can give me some help :) 

I know its not the cdrom drive because it works just fine in windows and Ive had to use my restore dvds to put vista back on and it worked perfectly.

Im thinking it has something to do with my computer having SATA drives because when the install first starts it tells me ATA1 and ATA3 failed.

---

### Post by inobe on 2008-11-27
first' are you trying to dual boot, also does that system contain a recovery partition ?

also, include make and model of this pc.

---

### Post by deathbyswiftwind on 2008-12-03
No I wasnt going to dual boot. Id prefer to be done with Vista and anything Microsoft in general. 

My system is an Acer Aspire M1100.
AMD Athlon 64 X2 4000+
4 GB DDR2 667Mhz Ram
350GB SATA drive
Nvidia 8600 1GB Video Card
Optiarc DVD-RW

EDIT:
Ah yes the system does have a recovery partition but I can delete it because the restore cds restore the recovery partition as well. I did it with an old version of ubuntu I put on here before. I cant run the older one and simply apt-get upgrade because none of my hardware was supported so I have no usb no network connectivity.

---

### Post by oldbaritone on 2008-12-09
I have the same machine, and just had a heck of a time flashing a new BIOS into it. "Standard" drivers don't seem to work with the CD/DVD, even when the system boots from the CD drive. I couldn't get Knoppix, Slackware, or FreeDOS to boot completely. They all bombed when they loaded the IDE and/or SATA drivers, and nothing recognized the CD from the OS itself. They came up running, but no CD/DVD in /dev - Only BIOS seems to recognize it.

I also have had problems with large (>2GB) usb keys locking the system completely, including in Vista, and during BIOS POST. That's why I was trying to upgrade the BIOS, but I haven't found a workable fix yet. Since it locks up POST as well as any OS, it must be a BIOS problem.

Only work-around that succeeded was a bootable USB key with DOS, made with the HP flash program. I still couldn't see the CD, but the BIOS was in the USB key. FYI.

---

