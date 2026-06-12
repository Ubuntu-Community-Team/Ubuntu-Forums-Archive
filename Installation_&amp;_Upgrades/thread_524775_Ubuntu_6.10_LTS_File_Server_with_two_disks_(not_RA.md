---
title: "Ubuntu 6.10 LTS File Server with two disks (not RAID)"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by dpol on 2007-08-13
I've run into an interesting dilemma with Ubuntu Server 6.06 LTS:  How do I use two internal hard drives to be recognized as just storage with Ubuntu Server installed?  

What I would like to do is to use the two hard drives that I have (a 100GB Western Digital and a 500GB Maxtor) to have some 600GB of storage on my fileserver.  I know that some of the 600GB will be used up by the Ubuntu installation and swap partition(s).  

I installed Ubuntu Server 6.06 LTS on my old PC.  The 500GB drive should be the master, but Ubuntu runs off of the 100GB drive.  I can mount the 500GB drive successfully in any directory on the 100GB's file system, but then when I browse to the 500GB drive, I see the same file system directory structure again.  It's as if the 500GB drive had another instance of Ubuntu installed.  

My guess is that I made a mistake when partitioning the drives.  Here is how the drives were partitioned:
the 100GB drive:
Partition 1 -- 92.8 GB
Swap -- 360MB
This drive is mounted at "/"

the 500GB drive:
Partition1 -- 465GB
Swap -- 430MB
This drive can be mounted anywhere in the 100GB drive's file system.  

Neither one of the two drives' capacities is adding up to their advertised capacities, making me think that I did something wrong.  

I am looking to just add the two drives as storage.  Does anyone know if I need to reformat, repartition, or just mount the 500GB drive somewhere else?  I am not interested in having RAID.  

Thank you.

---

