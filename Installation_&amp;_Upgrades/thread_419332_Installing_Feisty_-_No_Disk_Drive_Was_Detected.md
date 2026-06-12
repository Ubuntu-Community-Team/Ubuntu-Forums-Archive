---
title: "Installing Feisty - No Disk Drive Was Detected"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by thespursfan on 2007-04-22
Hello. I am using the alternate cd to install Feisty and I get to the point where it looks for my hard drive, and I am taken to a screen that say "No Disk Drive Was Detected..." And it asks me to choose a driver for my hard drive if I know it. I don't, so I chose ide-generic, and it didn't seem to make a difference.
Also, when I tried installing with the Live CD and it was time to edit my partitions, no devices were detected either.
It's just a plain WD120GB disk and edgy was able to install perfectly on it.
So, I'm baffled as to why Feisty would be having so much trouble finding it.

Any help or tips on getting this to work would be appreciated. Thank you!

---

### Post by thespursfan on 2007-04-24
Bump...

---

### Post by thespursfan on 2007-05-11
I still haven't found an answer for why this is happening.
Any ideas would be greatly appreciated. Thank you.

---

### Post by thespursfan on 2007-05-12
I think it's just a faulty hard drive. I may try another one and see if fixes the problem.

---

### Post by gentoo-user on 2007-05-17
I'm using the Ubuntu 7.04 server CD I burnt from the ISO I downloaded.  Same hard drive.  Tried a Western Digital hard drive, same problem.  My motherboard is an ECS P4S5MG.

---

### Post by gentoo-user on 2007-05-17
Another update, tried another PC with a MSI 845 Ultra motherboard, same problem with both the WD120 (120 Gigs) and WD200 (20 Gigs), same results.

Tried a Maxtor 6.4 Gb IDE drive (Model 90651U2), it detected it as SCSI drive!!!!  The following is from the gui installation screen

SCSI1 (0,0,0) (sda) - 6.4 GB ATA Maxtor 90651U2

It looks like Feisty doesn't like Western Digital drives.....

---

### Post by oozydigg on 2007-05-17
I doubt it is a WD problem.  I have a 120Gig WD SATA drive and I was able to do a Fresh install of Fiesty on it without any issues.  The drive and computer are just about three years old.

---

