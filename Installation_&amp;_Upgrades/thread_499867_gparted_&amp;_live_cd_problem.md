---
title: "gparted &amp; live cd problem"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by DraconPern on 2007-07-13
This is on 7.04 and it is an old problem in previous versions too.   Whenever gparted scans the drive, it mounts all partitions on the desktop.  Then when you try to apply an operation, it fails because they are mounted.  This problem manifests the moment gparted is run from the administration menu.  Looks like someone didn't do a QA check at all.  Will this be fixed in 7.10?

---

### Post by benjaminwr on 2007-07-13
you have to go into system > preferences > removable drives and media and disable

moutn removable drives and media when hot plugged, when inserted, and  browse when inserted.

the you can do whatever with g parted, remember to reenable then later :p

cheers

---

### Post by misterf1 on 2007-07-26
Cliffs:
Installing Fiesty for the first time
Trying to partition the usual "one big partition" into a dual boot/XP setup
Gparted CD's got issues (burned correctly 4x or less)
Gnome Part Ed on Fiesty Live CD won't partition

Hello first of all.  I'm running into the same problem.  As per usual, my drive has one large partition and I've followed the options for trying to make the /root, /swap, and /home partitions in addition to shrinking the windows partition for dual boot.  I get a fail on the operation.  I've read somewhere that the Gnome won't play with the partitions when they're mounted (which I didn't think they were when running the 7.04 live CD).  So I burned the Gparted Live CD image and ran that, but once I get through the options, the screen distorts and I can't see anything. Here's what I'm running:

AMD64 3200+ on Asus A8N-SLI board
2GB ram
two 300GB SATA drives (Fiesty is going on C, I've backed my stuff up)
two nVidia 7300GT's that have been SLI'ed and a DVI cable to the monitor

The only reason I think it might be the video driver is that the screen looks like it does when you plug the DVI cable into the wrong card (the secondary video card for SLI)

I hate asking dumb questions, but I'd love to get Ubuntu going at some point!!!  Thanks for running a great forum!

---

### Post by misterf1 on 2007-07-26
> **benjaminwr said:**
> you have to go into system > preferences > removable drives and media and disable

moutn removable drives and media when hot plugged, when inserted, and  browse when inserted.

the you can do whatever with g parted, remember to reenable then later :p

cheers

Hi there, I've tried your suggestion and I still get the same error (1080>1024) and then it tells me to try to resize a smaller portion.  Ideas?

---

