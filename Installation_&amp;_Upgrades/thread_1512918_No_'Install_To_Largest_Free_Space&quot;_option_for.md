---
title: "No 'Install To Largest Free Space&quot; option for dual boot"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by RitchieB on 2010-06-18
Hi there,
I recently downloaded Ubuntu 10.04 to use as a dual boot on my laptop.  After watching a dual boot tutorial video on youtube about ubuntu and windows, I have partitioned 30gb for Ubuntu.  However when I reboot my computer and try to install it I dont seem to have the option to Install it to the largest free space.  I really don't want to do the advanced install , at least with out guidance anyway, I am booting from a 4gb flash drive.  If you need an more info please ask as i would really like to use Ubuntu. 

Many thanks

---

### Post by darkod on 2010-06-18
If you made a partition from the 30GB in windows, that's not considered free space. You need to have unallocated, unpartitioned space, not belonging to any partition.

If you created a partition from windows it would be ntfs. Go into windows Disk Management and delete that partition.

After that the option will be available in the installer.

---

### Post by RitchieB on 2010-06-19
Hi, i had tried installing Ubuntu like that before partitioning the space.
This is the youtube video I used as an instructional [http://www.youtube.com/watch?v=OIoR7yp_nYc](http://www.youtube.com/watch?v=OIoR7yp_nYc)

I have enclosed a screen shot of my Disk Management NB i cannot delete the 2 smaller partitions on my hard drive as one of them contains recovery info and from what i have read the other contains important info too. My computer came with them already partitioned

---

### Post by wilee-nilee on 2010-06-19
Boot the live cd and take a screen shot of gparted which is in system-admin-gparted. Use the screenshot in ubuntu applications-accessories-take sceenshot use the select area to grab and capture just the gparted portion.

---

### Post by RitchieB on 2010-06-19
here is that screenshot

---

### Post by wilee-nilee on 2010-06-19
It should install to it, did you have it formatted before from windows and then deleted that partition after it wouldn't find the free space, and haven't attempted it again?

---

### Post by darkod on 2010-06-19
In this case the option is not available because you already have 4 primary partitions existing. The installer can't create a 5th partition, that's a limitation from the hdd.

You can either have 4 primary, or 3 primary + 1 extended partition.

You need to make a plan how to organize this. For example, move temporarily the data from your ntfs partition (not where windows is), then delete that partition, and after that create it as logical. That will create the extended partition. Then you can continue installing ubuntu and put the data back to the ntfs data partition which will now be logical.

---

### Post by wilee-nilee on 2010-06-19
Doh your right.;)

---

