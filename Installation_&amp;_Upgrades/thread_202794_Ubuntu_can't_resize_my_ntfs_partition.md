---
title: "Ubuntu can't resize my ntfs partition"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by oncomouse on 2006-06-24
This is my first time trying to use Linux.  That being the case, I want to dual boot with XP for now before I commit to Ubuntu.  I burned my own cd and that all went fine.  When I try to install, I run in to problems with the hard drive partitions.  If I choose the automatic partition option, it will just sit there "thinking."  I tried just letting it sit thinking it may take a while, but I went to bed and when I woke up 8 hours later it was still just sitting there with the working icon on the mouse.  I canceled out of the installation and tried again.  This time I thought I would partition manually.  I resized my XP partition leaving about 5 extra gigs there, then set up my Linux partition and left a gig for swap space following an online tutorial.  When I try to proceed from there, I get a message saying something to the effect that the installer can not resize the ntfs partition.  What are my options?  Am I doing something wrong?  Thanks for helping out a n00b.

---

### Post by Ubuntuud on 2006-06-24
gparted can't do so indeed. I believe diskdrake can though. You could download the PCLinuxOS live-cd image. Resize with it, and then do a Ubuntu installation.

---

### Post by Wormsie on 2006-06-24
I just used Partition Magic for Windows. :)

---

### Post by SkyNet2029 on 2006-06-24
Gparted does do a resize of an NTFS partition, although it should never take that long to do it. When I set up a dual-boot XP/Kubuntu box, I used the liveCD
version of Gparted, and I think that is where the differnce may be. Not sure if its
'ntfsprogs' gets installed or ships with Gparted, or if the liveCD has a full-featured version of Gparted.I have also killed an NTFS partition using the partitioner that ships with the Debian_installer (what Ubuntu uses). 

Anyways, some possible causes:
Your HD is just way too huge for the partitioner (like 2-3 terabytes).
OR
Your NTFS partition is seriously fragmented and it just takes that much 
longer to run disk-checks/resize if/when that happens
OR
Your HDD is on its last legs and linux is having a hard time actually reading/writing changes to it. (You could check the S.M.A.R.T. Status of your drive by way of windows using something like 'Belarc Advisor'. (It too is free)

---

### Post by aysiu on 2006-06-24
Theoretically, GParted can resize NTFS partitions, but I've found GParted in general (nothing to do with NTFS) to just not be that reliable.

DiskDrake has never given me any problems--no greyed options, no freezing.

---

