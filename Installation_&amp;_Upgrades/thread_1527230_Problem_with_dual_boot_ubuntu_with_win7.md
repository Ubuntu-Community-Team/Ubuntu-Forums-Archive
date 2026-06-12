---
title: "Problem with dual boot ubuntu with win7"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by drrkaplan on 2010-07-09
Recently bought hp dv7-3165 laptop with windows7-64 preinstalled. Ubuntu was able to resize the c-drive, but the resulting free space was 'unusable'. Aparently, sata drives can only have 4 primary partitions, & hp used all 4 in the windows install: sda1=200mb listed in fdisk as 'system', sda2=c-drive, sda3=d-drive(recovery), sd4=e-drive(FAT32 'hp tools'). If I delete sda1, system won't boot to windows, deleting only sda4 doesn't provide enough partitions for both root and swap, & it also would prevent me from using hp's recovery tools(no recovery discs provided). So far, I've been stuck.  I'm considering getting 2nd hd (this laptop has 2nd drive bay) &/or copy of win7(for clean install). I'm not sure if using the recovery discs I can make from the the provided app would just recreate the same problem.  I've looked at other new laptops, & most of them also have system or unlabeled partitions and recovery partitions.

---

### Post by someshwar_m on 2010-07-09
I second you. Similar problems, only the Laptop in question is a Lenovo G460 running Windows 7.

---

### Post by someshwar_m on 2010-07-09
Continuing on the same note, I wonder if it's possible to install Ubuntu on a dedicated partition that is not primary. If this solves the issues, it would be easy to create a dedicated partition within the extended partition, without screwing up the OEM's features of one-key backup and restore or the like.

---

### Post by garvinrick4 on 2010-07-09
> **drrkaplan said:**
> Recently bought hp dv7-3165 laptop with windows7-64 preinstalled. Ubuntu was able to resize the c-drive, but the resulting free space was 'unusable'. Aparently, sata drives can only have 4 primary partitions, & hp used all 4 in the windows install: sda1=200mb listed in fdisk as 'system', sda2=c-drive, sda3=d-drive(recovery), sd4=e-drive(FAT32 'hp tools'). If I delete sda1, system won't boot to windows, deleting only sda4 doesn't provide enough partitions for both root and swap, & it also would prevent me from using hp's recovery tools(no recovery discs provided). So far, I've been stuck.  I'm considering getting 2nd hd (this laptop has 2nd drive bay) &/or copy of win7(for clean install). I'm not sure if using the recovery discs I can make from the the provided app would just recreate the same problem.  I've looked at other new laptops, & most of them also have system or unlabeled partitions and recovery partitions.
In HP you should be able to download 3 dvds for your windows 7 and all the recovery disks you need. YOu can only make one set of 3 disks. You only need 1 primary for linux installs and that is a Extended partition and you can make as many logical partitions inside of the Extended and Linux will exist in Logical partitions. I will show you my HDD it is in a HP. Click on small picture. HP tools in a partition they are getting carried away.

---

### Post by garvinrick4 on 2010-07-09
You can also if you feel more comfortable get a small 250 gig to 320 gig portable USB drive. Install Ubuntu on that drive as sdb , make your partitions in gparted by booting off
your install CD and choose try Ubuntu and open gparted and make a small 300 meg or so sdb1 and choose /boot, Primary and ext4 as format. Make a 100 gig or so Extended Primary sdb2 format ext4 and then make a logical partition for / on and ext4 format of 10 gig or so. And then a big as you want /home in logical and ext4 format to keep documents and downloads music and such. No swap if over 2 gig of Ram.(swap is basically extra RAM on HDD) All other linux installs will
then be logical partitions in the Extended and will be able to use the /home already made.
The first logical partition starts at sdb5 and on up. Primarys like to be sdb1 thru sdb4. 
This will only use 2 primarys installing this way. And always, always on last page of install in advanced button on bottom right of page choose sdb not sdb1 or sdb5 but sdb
 If installing on internal drive and is sda choose sda to put boot in on last page of install.
This is Very Important to make booting in grub2 the Ubuntu of choice work correctly. It is 
easily fixable but no reason to put in wrong place. All partitions can be resized later if you find need.
 When you first boot into Ubuntu no matter if on internal or external use this to get all installs in grub menu (boot menu)

```
sudo update-grub
```

---

### Post by someshwar_m on 2010-07-12
Hi [drrkaplan]("http://ubuntuforums.org/member.php?u=1109498"),

My issue has been resolved!!! I am able to dual boot Windows 7 and  Ubuntu (and I have now added a Fedora as well). The issue I discovered  is that (don't know why or how) the extended partition had a wrong size  in the partition table. So, the total size was exceeding the disk size.  The partitioning software used to factory-create the 3 primary and 1  extended partition was thus responsible for the error in my case.  Because of this, gparted was unable to understand the existing  partitions and assuming a blank HDD.

I used information from this page  ([http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)) to rectify the error.  In this article, the author gives an example of screwing up the  partition table (just for the learning) and getting it right. It seems,  the OEM partition table appeared to be screwed in the exact same fashion  in my case. Please try this out!!

Love Ubuntu!

---

### Post by thahir1986 on 2010-07-12
i have the similar problem with my hp laptop...now solved

thanks

---

