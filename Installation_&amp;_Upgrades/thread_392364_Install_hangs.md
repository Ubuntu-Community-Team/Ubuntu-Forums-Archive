---
title: "Install hangs"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by Septimusx on 2007-03-24
Hi all. Thanks for taking the time to read this. I'm interested in trying out Ubuntu 6.10, in a multi-boot enviroment, XP, Vista, and Ubuntu. XP(my old faithful in case I need access to internet/drivers), Vista(checkin it out, possibility of replacing XP), Ubuntu(possibility of replacing MS!) My current setup is MSI-PM8M-V, Intel P4 3.0g, PNY GeForce 6600, 1gig of ram, 1 80g IDE HD partitioned into 3 equal partitions, with XP and Vista on the 1st and 2nd partition with the 3rd being reserved for Ubuntu, and a 160g SATA, which I'd like to use as the main storage drive. I downloaded the ISO, checksum was good, followed the directions to burn the image, and rebooted. The Ubuntu boot screen comes up no problem. First time, I chose Start/install- It got as far as an orange screen, with a white square in the corner. Re-booted, chose the safe option, got to the orange screen with the white box again. Only this time I was able to read the white box. It mentioned some sort of error about the GNOME desktop. Unfortunately in my elation to be able to read the box, and the possibilty of the install working, I didn't pay much attention to what the box said. On with the installation- I got thru GParted, where I set a 2gig /, and a 1 gig /swap in the unallocated space I had reserverd for Ubuntu. That seemed to go just fine, and into the file copying process it went. Where it only made it to about 24% and locked up. Any ideas as to how to proceed next would be greatly appreciated!

---

### Post by eapache on 2007-03-24
Run the verification on the cd itself (third or fourth menu option?). The download was good, but the burn itself often gets messed up. What speed did you burn it at?

---

### Post by Septimusx on 2007-03-24
I ran the cd verification from the Live CD and it said all was well and dandy. I burned it at 32x I believe it was. I tried using the F6 option and removed splash from the config and it ended up giving me a [17179636.140000] <0>Kernel panic - not syncing: Fatal exception in interrupt. I saw this in another post and followed the suggestion on adding linux ide=nodma. That got me into the beginning of the desktop only to have the white box appear and it all locks up again. I've only been able to get as far as the partitioning/mounting/file copying once. Every other time ends up in a lock.

---

