---
title: "Installing ubuntu on existing partition for dual boot"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by Bolognaman on 2008-02-08
I've read through countless threads, but have not been able to find a definitive answer.
I would like to install Ubuntu 7.10 onto my machine which currently is running winxp.  I need to keep it a dual boot system for familiar programs/family members using computer.  I have two hard drives inside my machine:
A maxtor which is about to bite the dust due to bad sectors, and
a seagate which I partitioned into two drives.  Both disks are NTFS.  So, in windows terms I have  C, F (200 gb), and G (100 gb) drives,  (D and E are my dvd, cd drives).  When I try to install Ubuntu I see both hard disks in their entirety, but am not sure if I am looking at the partitioned seagate and if so, which partition.  What I see is:  
sda for the maxtor
sdb for the seagate with (0,0,0) and Partition 1
Does Ubuntu start counting with 0 or 1 for the partitions?  and what are the 0's referring to?
I have nothing on my G drive and would like to dedicate it solely for Ubuntu, but I don't want to risk messing up winxp, mostly because I have just had to reinstall EVERYTHING for the third time due to faulty hard disks. 
Thanks for the advice.

---

### Post by Pumalite on 2008-02-08
Boot your Live CD and from the Terminal, post the output of:
sudo fdisk -lu

---

