---
title: "How Split HD into equal size?"
date: 2021-09-09
forum: Installation &amp; Upgrades
---

### Post by mawil10132 on 2021-09-09
Solved, started over, located the Install Beside which automated the process.

Doing install Ubuntu 20.04, at HD partition modification. I want to evenly devide This is what I see.
Free space Size 1MB,  
/dev/sda1 ntfs Size 523MB Used 448MB, /dev/sda2 EFI Size 104MB, Used 33MB Windows boot manager, 
/dev/sda3 Size 16MB Used Unknown ( I suspect it's Thumb Drive), 
/dev/sda4 Size 479457MB Used 90272MB, 
free space Size 0MB.   

Then at bottom off chart: Device for boot loader installation; /dev/SDA  ATA WD easy store 480 (480.1GB)      

Once I know the value to decide HD, which one do I check, then assumed tap on New Partition Table.. ?At which point there's some entry box to enter the HD one half of size?  
Igmur of Partitions; [http://imgur.com/a/zI89G6q](http://imgur.com/a/zI89G6q)

---

### Post by mikewhatever on 2021-09-09
You need to shrink /dev/sda4. Forget about "Split HD into equal size" for now. Make sure Windows is shut down.

PS: How hard is it to post info in a readable format?
```

/dev/sda1 ntfs Size 523MB Used 448MB
/dev/sda2 EFI Size 104MB, Used 33MB Windows boot manager
/dev/sda3 Size 16MB Used Unknown
/dev/sda4 Size 479457MB Used 90272MB, free space Size 0MB

```

---

### Post by mawil10132 on 2021-09-09
Thanks for tip, it's stupidity on my, I don't do stuff like. If I understand u correctly; highlight SDA4, tap on continue, 'shrink' SDA4 to 239,728MB?  So, I did this and got this, see igmur image; http://imgur.com/a/BIxvFtb 

What's happening now when I Tap Install Now is the message; No Root filed system is defined. Please correct this from the partitioning menu.

---

### Post by ActionParsnip on 2021-09-10
/dev/sda is the storage itself. a different drive would have a different letter like /dev/sdb
The numbers are the partitions on the drive
1 - 4 are primary partitions
5 is the extended partition
6 and higher are the logical partitions in the extended partition

You have /dev/sda1, /dev/sda2, /dev/sda3 and /dev/sda4 so you have 4 primary partitions on the same disk. No thumb drive

---

### Post by The Cog on 2021-09-10
It's my understanding that one of the four primary partitions has to serve as the "extended" partition which then becomes a container for the "logical" partitions 5 and upwards.
This command will help to visualise your disks:
```
lsblk -p | grep -v snap
```

---

### Post by grahammechanical on 2021-09-10
> Once I know the value to decide HD, which one do I check, then assumed tap on New Partition Table.. ?

Do not click "New Partition table! That will apply to the whole of the drive (sda) and not just to one partition of the drive (sda4). You will lose everything on sda.

What do you want to do? Do you want to shrink sda4 (ntfs format) creating unallocated space? Which you then use to create a Linux partition (Ext4 format) to install Ubuntu in?

Here is the rule to follow. Use Windows tools to manipulate Windows partitions and Linux tools to manipulate Linux partitions. Use a Windows tool to defrag the hard drive and make sure that Windows still loads. Then use a Windows tool to shrink sda4 to create unallocated space. Make sure that Windows still loads

Run Ubuntu in live/Try session and use GParted to create A Linux partition or two to install Ubuntu in when you then run the Ubuntu installer.

GParted is installed by default in the Ubuntu Try session. Here is information on how to use it.

[https://gparted.org/](https://gparted.org/)

Regards

---

