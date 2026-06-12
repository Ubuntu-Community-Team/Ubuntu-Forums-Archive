---
title: "Partitioning Advice"
date: 2005-08-16
forum: Installation &amp; Upgrades
---

### Post by ace2005 on 2005-08-16
I need some advice on the mount points to use with my hard disks

I'm getting rid of XP and installing Ubuntu or Kubuntu,

Primary Hard Drive 20GB, Secondary Hard Drive is 10GB (the 80GB one is for file storage, i have all my work on it and thats going to be mounted on /mnt/work/)

I want to use both the 20GB and the 10GB disks so what mount points do i use, do i use a root partition and a /home partition, or a /usr or what on which drive?

Or is there a way i can make both disks act like one and be /

---

### Post by DJ_Max on 2005-08-16
I'm not sure you could make both HD's act as / without using RAID. You could make one hd /, and one /home.

---

### Post by ace2005 on 2005-08-16
I don't want to give /home its own partition, i store everything on /mnt/work (the 80GB one) Its a single user system and my home directory is almost empty. I'll try /usr and / If that does not work i'll reinstall.

---

### Post by wrtrdood on 2005-08-16
/usr is a good choice.  It used to never fail that I would make it too small.  Usually the best way to leverage different devices is to consider where to keep things you want separate, both for backup and redundancy.  For example, I keep all my personal stuff under /home.  Having that on a different device gives me a lot of flexibility when I test different distributions.  I never have to touch it.  /var is the only other "system" directory I'd put somewhere else.  Keep in mind that maintaining such a configuration can get to be a headache at times.  You know... when you forget to keep a copy of fstab or a listing from fdisk -l ...things like that.   :)

---

### Post by jfdill_2 on 2005-08-16
[QUOTE=DJ_Max]I'm not sure you could make both HD's act as / without using RAID. You could make one hd /, and one /home.[/QUOTE]
There's an easier way and that is to use LVM2 which is supported in the installer.  I have tested it a lot lately on Ubuntu and Debian and it works very well.  Most important /boot should be on a separate, regular partition since GRUB / LILO don't totally understand LVM correctly.

For the first case of 20 GB and 10 GB hard drive, you could do something like this:

First hard drive:
Primary partition #1 128 MB /boot ext3
Remainder of space Use as -> LVM

Second hard drive:
One large partition Use as -> LVM

Create a Volume Group and add that LVM partions of 1st and 2nd hard drives to the VG.

Now you can go to the LVM entry at the top and create Logical Volumes for each filesystem that you want separate, split up however you want, regardless of the physical layout of the drives.  I usually make one for "/" and one for swap and separate for "/home" since I would not want to reformat that if I install the OS again.

I suggest not using up all of the space and making the logical volumes a little bit smaller than you think that you will need--Thanks to the magic of LVM2 :) you can increase the size of the Logical Volumes and the filesystems on them later, that way you do not have to guess in advance how much space each one will take.  With certain filesystems, it is even possible to "shrink" the size of the filesystem later and the logical volume to free up more space to increase another LV.

Relevant links:
[LVM HOWTO](http://www.tldp.org/HOWTO/LVM-HOWTO/)
[Extending a logical volume](http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html) is ridiculously easy to do, adjusting size seems to work best with ReiserFS
[SystemRescueCD](http://www.sysresccd.org/) is the easiest Linux rescue CD that I have found for support of LVM2
[LVM2 in Knoppix](http://www.knoppix.net/wiki/LVM2) is also possible, but I think you have to "install" it to the hard drive first

---

