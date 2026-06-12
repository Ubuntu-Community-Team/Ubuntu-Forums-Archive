---
title: "Partition Resizing Oddity"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by stopgear on 2012-03-22
I have Ubuntu 11.04 installed  on some older hardware that functions as a NAS unit with SAMBA. It also doubles as a home for a GTX 260+ I'm using with BOINC (don't have anywhere else to put the dinosaur). 

As it was going to be a NAS unit, I gave Ubuntu only 3.7 GB, where I originally meant to give it 6 GB. I didn't think much of it until I updated to 11.10 and ran out of space. I took the drive out and re-sized it with GParted on another machine, deleting a 140GB+ partition, resizing and moving the swap space, and then resizing the boot partition. I then created the 140GB flat partition as seen in the attachment.

What is odd is GParted, as run on the NAS unit, reports a 6GB partition (filesystem?), where in system monitor, the same filesystem (partition?) is listed as 3.7 GB. the same amount of unused/free space is present at both locations. Disk utility agrees with GParted.

Any ideas on how I can fix this? Does this illicit another reinstall?

Thanks for the help!

---

