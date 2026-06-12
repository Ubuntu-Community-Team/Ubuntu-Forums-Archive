---
title: "Help installing Ubuntu 10.04 on my already partitioned HDD"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by Preston Durbin on 2010-10-18
I have partitioned my HDD to give it a 30GB location for Ubuntu 10.04. I just need to know what steps to take to install it to the drive I partitioned for it. Someone please help

---

### Post by dhavalbbhatt on 2010-10-18
> **Preston Durbin said:**
> I have partitioned my HDD to give it a 30GB location for Ubuntu 10.04. I just need to know what steps to take to install it to the drive I partitioned for it. Someone please help


At the time of installation, the partioner within Ubuntu will ask for what partition to use to install Ubuntu 10.04 to. At that time, you can select the partition of your choice. If the partition has detected this free space (assuming it is free space), it will show up as one of the "guided" options, if not, then you can select it manually. 

Dhaval

---

### Post by Naitsirhc Hsem on 2010-10-18
when you are in the install process, it will scan the partitions on your hard drive.  when it gives you the option to erase the entire disk, use free space or partition manually, choose partition manually.  how much ram do you have.  if it is more then 2 gb, you do not need a swap partition.

if you need a swap partition, resize your 30gb partiton and make a gig or so of free space.  then format the free space as swap. 

next, format the 30gb partiton as EXT3 or EXT4 and set the target/mount point to /

your'e done, continue with the installation

---

### Post by Preston Durbin on 2010-10-18
Finally after 3 days... i did it a little differently then what you listed but i got it done :) thx for the help

---

