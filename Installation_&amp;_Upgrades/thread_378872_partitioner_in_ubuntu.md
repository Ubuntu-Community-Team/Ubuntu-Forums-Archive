---
title: "partitioner in ubuntu"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by eyebrow on 2007-03-07
so i have windows xp 64bit installed and i cant partition drives in it because there doesn't seem to be any 64bit partitioning programs.  so i want to use the partitioner in Ubuntu.  i cant figure it out.  

1. i choose the drive - 160gb sata with xp installed (60gb used)
2. it asks to create root - i do the "/" and it says i have no root
3. i know i need a swap - but if i select the drive for both thingys (sorry for the non-tech jargon) it says i cant do that.
4. i get the idea that i have to use the whole drive - shouldn't i be able to select the amount?


is there a walk through i can download for the partitioner.

---

### Post by liamtoh1 on 2007-03-07
Have you seen [this]("http://www.psychocats.net/ubuntu/index")?

I was searching for some info my self a few days ago, and found the above site. I was able to install Ubuntu 6.10 on my desktop pc (dual boot XP Pro). 

GParted is the software that will allow you to partition your HDD. 
This software (i believe) is on the LiveCD. 

Hope this helps.

---

### Post by etank on 2007-03-07
gParted is on the live CD. If that doesn't work for you then you may want to look into downloading from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). I think that the version on the Ubuntu CD is not as new as the one from the gParted project.

---

### Post by mrfelker on 2007-08-22
There are issues with Ubuntu's Partitioner.  I have a 64-bit system (probably not a factor).
I have installed Fedora and Suse as RAID 0.  When I try installing Ubuntu as RAID 0 (or RAID 1) for that matter weird things show up configuring RAID - like RAID devices that don't exist - can' read one of software RAID partition.   Once I even had an existing RAID called "Cancel"!  Other lots of other times I've had trouble with the partitioner in terms of RAID.  Of course I'm using the Alternate text install and I'm using Ubuntu 7.04.  My multi boot program is Terabyteunlimited BootITNG (great program) but even that has a problem - even if I delete a Ubuntu partition the  partition table has entries that should have been corrected by Ubuntu (other distro's do this easily).  I finally have a RAID 0 Ubuntu system (total disk space 60GB) but I had to ignore serious warning from the partitioner.  Anybody else run into this.  It may be a holdover from the Debian installer??

---

