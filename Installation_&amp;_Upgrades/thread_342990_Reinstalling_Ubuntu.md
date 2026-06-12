---
title: "Reinstalling Ubuntu"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by Kelnoky on 2007-01-20
So when I installed this Ubuntu a few months back I was a total Linux noob. Now that I've gotten a little more into it, I can see that I have messed the poor Ubuntu up. Badly. Too much stuff installed, its running slow here and there, although I am using fluxbox and all kinds of stuff is weird.
So I want to reinstall the whole thing. The Problem is, my /home is on the same partition as my root stuff. Some info on my hard drives: 

shaolin@Tuska:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        8924    71673997+   f  W95 Ext'd (LBA)
/dev/sda2   *        8925       30401   172514002+   7  HPFS/NTFS
/dev/sda5               2        1913    15358108+   7  HPFS/NTFS
/dev/sda6            1914        8924    56315826    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36103   289997316   83  Linux
/dev/sdc2           36104       36481     3036285    5  Extended
/dev/sdc5           36104       36481     3036253+  82  Linux swap / Solaris


So you see, sdc is my Linux partition, the other two hdds were Windows stuff, but now its only a huge 500GB wasteland, I dont need any of the data which is on those two hard drives anymore. So my idea was, format the sdb drive and you can story your /home there. That I did but when I mount it now its only accessible for the root. But thats a minor problem.
Because the MBR is on sda. Which actually is a useless partition, data wise. But now I cant just reformat it...right? 

Other Issues: The space on sdb should be enough to backup my stuff - but what to backup? Ok, the personal files from my /home dir, yes. But where else are important files I might want to get over to the new Ubuntu?
And is there something very important I might be missing about the whole reinstalling concept? :D 

Sorry for the whole load of questions, but I'm hoping you can help me with most of it. :)

---

### Post by Kelnoky on 2007-01-21
*push*

---

### Post by Pobega on 2007-01-21
So can't you resize some of your current partitions, make a new partition, mount it from within your current Ubuntu install, then bring everything you want from /home over to it? Then reinstall Ubuntu on your bootable partition, and then change your /etc/fstab from the LiveCD (Before booting into your system).

---

### Post by warjowuch on 2007-01-21
Is there not a possibility to reinstall onto the old used partition (over the old installation), and that it keeps your home?
But, warning: it might be that your system is also slow because of messed up configs in your home...

---

### Post by Kelnoky on 2007-01-21
Well, I think only installing a new Ubuntu over the old one wouldn't do the trick. I wanna have a real fresh start actually.

@Pobega
So, ok, I saved lots of data from my current /home to another hard drive. Assuming I got everything from /home I need as data - there is nothing left worthy of beeing saved, right? So theoretically I could insert a LiveCD, wipe out my current Ubuntu hard drive, repartition it and have a new OS?
Even besides the fact that I sure will forget to save some piece of important data, I'm always uneasy when I have to format a whole drive. :D

---

### Post by warjowuch on 2007-01-24
Well, it depends on whether or not you configured your fstab, your xorg.conf or so. These can of course be reconfigured... Or install partimage into a livecd and image your drive in case of disaster. But, your assumption of inserting a livecd and install/repartition the whole thing is also true, you can!
So, good luck!

---

