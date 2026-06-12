---
title: "Disk Space"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by LAF4SENS on 2007-11-05
Hi,

I've installed Ubuntu 7.10 on my PC. I have 2 old hard drives.

Hard drive 1 is 8 Gigs (don't laugh !!) and contains the ROOT file system (all of the OS).

Hard drive 2 is 30 gigs (a bit better !!) and is set has /media/sdb1.

Now when I install  software It never asks me on which disk I want to put in on. Is this normal?

Being from the WINDOWS school (unfortunately), it always asks where you want to install the software.

I'm just affraid that HARD DISK 1 is going to get filled up, and problems are going to arise. 

Is there a way to tell the software to install on HARD DISK 2??


Thanks in advance,

Marc.

---

### Post by Fire_Chief on 2007-11-05
Hi Marc, 

You are correct. Since the first hard disk is mounted as the root for the system ( / ), then all the typical sub-directories that store various app components (/usr,  /lib,  /opt,  /var, etc.) are also there. Your second disk (mounted as /dev/sdb1) will not hold any of the apps you install. It will not ask you where to install apps and there is not a way to specify. This is normal behavior.

There are a number of re-partitioning schemes you could implement to alleviate your concerns about disk space (ah the beauty of complete flexibility). I won't go into them all here simply because your options are pretty large.

This article explains a good bit about what most of the top level directories hold and how much space they typically use.  He does go a bit overboard with partitioning in terms of what I'd suggest for a home user but to each his own.
[http://www.linuxsa.org.au/tips/disk-partitioning.html]("http://www.linuxsa.org.au/tips/disk-partitioning.html")

You may also want to reference this page on separate home partitioning. [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

Cheers!

---

### Post by LAF4SENS on 2007-11-05
Thanks Fire Chief,

How do I repartition my hard drives without loosing what I installed so far? Is this possible?

Thanks,

Marc.

---

### Post by Fire_Chief on 2007-11-05
Except for resizing a partition, all other partitioning activites destroy the data located on them. You can copy the data to a different location (read separate partition or physical drive) to save it temporarily while you re-partition and re-format the target drive (i.e. copy any data from the 30 GB to the 8GB while you re-partition the 30GB, then move data back to the new permanent locations on the 30GB). Of course, be sure the data you want to save fits in the temp storage location. In *most* cases, the only data you need to save is your home directory contents for users on the system (could grab all of /home to be safe).

---

### Post by rsambuca on 2007-11-05
Unless you are going crazy installing stuff, 8 GB should be more than enough.  You might consider copying your /home to the larger drive and linking it, but in shouldn't be a necessity since you are using the larger drive for your media files.

Basically, I think you should be fine.

---

### Post by LAF4SENS on 2007-11-05
> **rsambuca said:**
> Unless you are going crazy installing stuff, 8 GB should be more than enough.  You might consider copying your /home to the larger drive and linking it, but in shouldn't be a necessity since you are using the larger drive for your media files.

Basically, I think you should be fine.

I'm new to all this LINUX stuff. But I have to install ORACLE database and some tools, which takes up lot's of space. I would me more confortable having all this software reside on my bigger drive (30 gig).

You talked about copying the /home directory to my 30 gig drive and linking it....

How would I do that ?

Thanks,

Marc.

---

### Post by Fire_Chief on 2007-11-05
See my previous post for the separate /home partition how-to (web link).

Your Oracle DB Installation should let you specify where to install the DB files (I think it defaults to /opt). In this case, you could have the 30GB partitioned into 2 partitions. One for /home and the other for /opt or whatever you want to call the Oracle DB location. (/db ?)

The Oracle tools probably won't fill up the 8 GB drive so you shouldn't have to worry about moving your / partition.

If you're not sure about the current disk usage you can run```
sudo df -h
``` It will spit out a nice read out for all of your partitions mounted in Linux and their usage.

---

### Post by sloe on 2007-11-05
Ahhh, Oracle...finally, something I can contribute a semi-knowlegeable response to.

the Oracle Universal Installer is fairly easy to work with, and it does give you the choice of where to stick stuff in the file system.  If you're feeling really fancy, you can even tell Oracle to use it's own internal file system format and write directly to the disks (kind of like a RAW format), but that is way too advanced for piddly little systems like ours.

Anyhow, as Fire_Chief said, Oracle sticks a little bit of info, mainly the inventory and some control files, in /opt.  The Oracle binaries and data files are the ones you get to specify the location of - my usual layout is a partition (or just a directory off of root) on the root drive called /oracle for the binaries, and a partition on the big drive called /oradata.

The Oracle binaries will eat up about 1.6 gig if you install the database, application server, and web utilities (standard install, I think), and the data files will take up as much space as you tell them to.

Like I said, the Oracle installer is very easy to work with and very flexible.  One thing I want to suggest, however, if this is going to be used as a production database, put your redo logs on a separate drive from the data files - in other words, here is my suggested layout:

/dev/sda1 6GB mounted as /
Oracle binaries in /oracle
/dev/sda2 1GB mounted as /ora_redo
/dev/sda3 1GB mounted as swap
/dev/sdb1 10GB mounted as /home
/dev/sdb2 18GB mounted as /oradata
/dev/sdb3 2GB mounted as swap

If your DB isn't very big or active, the 1GB for redo may be overkill, so adjust accordingly.  I've suggested 3GB of swap because Oracle, and all of it's java code, eat up A LOT of memory.  If you can afford the space, go ahead and bump swap to 4GB, or leave it at 3GB if you've got a gig of RAM (and/or a 32 bit processor).

If there are some real DBA's or DBE's out there that can correct me, fire away.  This is all relative from my experience of installing Oracle on Sun 480s, 880s, 6800's and 15k's with terabytes of attached storage.

-sloe

---

### Post by LAF4SENS on 2007-11-05
Ahhhh,

Sure feels good to talk ORACLE !!!!

Thanks, I give this a try tonight at home. 

Hope we discuss Oracle in the future :KS

Thanks Sloe,

Marc.

---

