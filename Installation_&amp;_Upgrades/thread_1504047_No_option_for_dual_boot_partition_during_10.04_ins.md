---
title: "No option for dual boot partition during 10.04 installation"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by wilwil0 on 2010-06-07
I am trying to install Ubuntu 10.04 LTS on a Windows XP Media Centre Edition system.

On the Step 4 of the installation which usually gives you the option to partition the disk but it only gives me the option to Erase the entire disk or specify partition manually, although this also doesn't allow anything other than totally erasing the disk. I'd ideally like to keep my Windows and I have installed Ubuntu before (but 9.10) on a different system.

Does Ubuntu 10.04 LTS not offer this or is there something wrong with my disc and should I re-burn it or something?

---

### Post by subodh.rohilla on 2010-06-07
Choose specify partition manually option and install ubuntu in any partition **other than** windows xp partition.

After installing ubuntu when you will restart your system it automatically shows dual boot menu in which there is option for both xp and ubuntu.

This menu will always be there when you will start your  system

---

### Post by wilwil0 on 2010-06-07
Thank-you for your reply.

That's what happened when I installed 9.10 on a different system and it worked perfectly.

I can't specify a partition on this one because it doesn't allow me to select or resize any other part of the disk it is erasing. It simply selects it all, doesn't allow me to create a different partition or resize it. I was wondering if it was something about it being 10.04?

---

### Post by darkod on 2010-06-07
Probably you have the maximum of 4 primary partitions on the hdd, so it can't offer to install ubuntu into a new partition.
Boot into live mode and take a look with Gparted.
Or in windows open Disk Management. Don't rely on the partitions (drives) shown in Computer, some partitions are ignored by windows but they are counted in the maximum of 4 primary partitions too.

---

### Post by wilwil0 on 2010-06-07
Here is a print screen of it.

[http://i50.tinypic.com/14o67ih.jpg](http://i50.tinypic.com/14o67ih.jpg)

---

### Post by kansasnoob on 2010-06-07
Rather than trying to install choose to try without changes, then either post a screenshot of Gparted or the output of:

```
sudo fdisk -l
```

Or if you have only one hard drive:

```
sudo parted /dev/sda print
```

---

### Post by wilwil0 on 2010-06-07
OK I'll try that.

---

### Post by wilwil0 on 2010-06-07
Results of "sudo fdisk -l" :
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23440   188281768+   7  HPFS/NTFS
/dev/sda2           23442       24321     7068600    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 
 
Result of "sudo parted /dev/sda print" :

> ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA SAMSUNG SP2004C (scsi)
Disk /dev/sda: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  193GB  193GB   primary  ntfs         boot
 2      193GB   200GB  7238MB  primary  fat32        lba

Here is a screenshot of the GParted, I don't really think this looks to healthy...

[http://i48.tinypic.com/16bc3ko.png](http://i48.tinypic.com/16bc3ko.png)

It says to run "ntfsclone --rescue ..." but that yeilds no results, I'm guessing because I don't know what to put at the end of "rescue" instead of the "...".

---

### Post by darkod on 2010-06-07
Did you try booting XP and running the

chkdsk /f /r

---

### Post by wilwil0 on 2010-06-07
No, I haven't been able to boot it up onto Windows XP, could a few days ago however. This happened before though and it started working again.

I think the errors on the disk are also what is causing it to not boot up.

Could I run "chkdsk /f /r" from a Windows boot CD?

---

### Post by darkod on 2010-06-07
> **wilwil0 said:**
> No, I haven't been able to boot it up onto Windows XP, could a few days ago however. This happened before though and it started working again.

I think the errors on the disk are also what is causing it to not boot up.

Could I run "chkdsk /f /r" from a Windows boot CD?

Yes, from the Recovery Console you should be able to run it.

---

### Post by wilwil0 on 2010-06-07
I think I know where my boot cd is so I'll try it.
Thanks for all the advice.

---

