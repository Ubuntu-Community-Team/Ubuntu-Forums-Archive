---
title: "Ubuntu does not recognize second HD"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by RIES on 2010-01-31
Hello,
 
I just installed Ubuntu 9.10 on my system that ran XP. I used the installation CD and installed directly over XP.
 
Everything went smooth and Ubuntu seems to run fine. The only con is that it cannot detect my second (or first?) harddrive anymore. Under XP I had 2 harddisks, one 80 GB where the OS ran on, divided in two partitions C and D. Win XP ran on C, D (same disk) was used to store data on. E was the second HD and was mainly filled with MP3's. I detect the two previous C and D partitions as filesystems and no data seem to be lost. However I can't find the second drive anywhere (the former E disk).
 
I have no clue how to find it, do I have to mount it somehow? Since I'm brand new to Ubuntu any help will be most appreciated. I tried the sudo command which returns some information on the 80Gb and the 60 Gb disks but I don't know how to interpret it...
 
:confused:

---

### Post by darkod on 2010-01-31
Are you sure you installed over XP? You say you can detect now C: and D: as filesystems. If you installed over XP that would destroy C:.
Could it happen that you installed on the former E: and that's why you can't see it now, and you can see C: and D: partitions in Places now.
Alternatively, in terminal execute:
sudo fdisk -l

and post the results here.
You should be able to see any ntfs partitions on all drives in Places. It would probably say like 50GB filesystem first, until you click on it and it will ask you for your ubuntu password to mount it. After it's mounted, you can browse it from within ubuntu.
There is procedure for a ntfs partition to be automounted at start if you plan to access it regularly.

---

### Post by RIES on 2010-01-31
Here it is...from the looks of it you might be right?

Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca6cca6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6995    56187306   83  Linux
/dev/sda2            6996        7299     2441880    5  Extended
/dev/sda5            6996        7299     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88428842

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        9728    57657285    f  W95 Ext'd (LBA)
/dev/sdb5            2551        9728    57657253+   7  HPFS/NTFS

---

### Post by darkod on 2010-01-31
Well, if the 80GB was the one with XP on it, you can clearly see it's /dev/sdb in linux terms. And both ntfs partitions are there.

Ubuntu is actually installed on the 60GB. I hope you had a backup of those MP3s. Otherwise, sorry to say but it seems you overwrote them. :(

---

### Post by RIES on 2010-01-31
I have a backup, no problem :D!

But if Ubuntu installed on the former E disk, than I can no longer access it to store other data? In other words, it's not available as a filesystem like the other disk? I mean, if Windows installs on a single disk you can still access that disk to store data, why can't I find this HD in Ubuntu?

Thanks for helping out!

---

### Post by darkod on 2010-01-31
What do you mean you can't access it?
You have all of /dev/sda available in ubuntu, it's taken up by your / partition (and some small space for the swap partition). So you have almost 60GB in /.

You can put music in your Home folder, in Music or however you want to organize it.

As for /dev/sdb, you need to decide whether you would like to use it as ntfs (as it is right now), or reformat the partitions in ext4. Right now, you can find it in Places and open those ntfs partitions and read and write to them.

---

### Post by RIES on 2010-01-31
You're right, I see it now...

Everything seems fine, only thing I would like to do is get rid of the 2 partitions on the 80G disk. Can I do this from within Ubuntu or do I have to reinstall?

Thanks again!

---

