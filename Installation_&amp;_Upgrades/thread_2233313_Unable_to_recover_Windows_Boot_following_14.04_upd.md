---
title: "Unable to recover Windows Boot following 14.04 update"
date: 2014-07-07
forum: Installation &amp; Upgrades
---

### Post by Peterlorre on 2014-07-07
Hi All, 

Until just a few days ago I was running a dual boot of Ubuntu 14.04 LTS and Windows 8.1. After the last update I am unable to boot into windows, however, even manually (the windows entry isn't listed among the boot options). I have tried recovering with a windows recovery cd, but Windows reads the disk as locked and can't repair it. I've also tried the widely-cited boot-repair-disk utility, which doesn't seem to do anything but send me to a blank screen after I boot into it. Can anyone make a recommendation about what to try? At the moment my priority is getting windows working again, as I am confident that I can get ubuntu running again thereafter. 

Thanks for your help. I'm using an HP Envy (x64 i7, 16G)

---

### Post by ubfan1 on 2014-07-08
Have you tried the EFI boot menu (at power-on, some function key, or ESC or DEL, varies by machine) to get to a list of devices and OSes to boot?
Sometimes, you need to select the hard disk, then get a choice of OSes.

---

### Post by Peterlorre on 2014-07-08
Yes, only Ubuntu is displayed in the EFI menu.

---

### Post by Peterlorre on 2014-07-08
Ok, this is concerning- I've looked around more and it appears that ubuntu has eaten my windows partition somehow (lsblk shows that my hard drive has only one partition now, which comprises my entire hard drive). 

Obviously, this seems like a bug... any ideas as to how this could have happened? Has anyone else experienced this? 

I guess I'll begin a total reinstall.

---

### Post by Peterlorre on 2014-07-08
Wait, it looks like the partition is only 930G, so it's possible that the windows installation is still there but the partition has been resized. Does anyone have an idea about how to tell if this is true or not, and potentially how to recover from it? I'd really rather not spend a day reinstalling everything.

---

### Post by yancek on 2014-07-08
>  even manually (the windows entry isn't listed among the boot options)

Did you use the down arrow on your computer to assure yourself that you have seen all the menu entries?  I expect with a new install of Ubuntu 14.04 and just windows 8, there would not be many entries so easy enough to verify.

 Do you get the same error with a windows installation DVD (device locked) or do you have one?
It isn't clear from your posts if you can boot Ubuntu, can you?  If so just run:  sudo update-grub and watch the output to see if you get a windows entry.
You can use gparted from a terminal to check partitions, if you have GPT partitioning, fdisk won't provide accurate output.  Also try:

sudo parted /dev/sda print all, that should output information on mounted and unmounted partitions.
It's strange that a simple update on a recently released version would cause this sort of problem.

---

### Post by Peterlorre on 2014-07-08
Sorry- I can boot ubuntu, and I do so by default when I power on the computer (previously I had to manually select ubuntu as a boot option or else the computer would default into Windows). As Far as I can tell everything is fine in my ubuntu OS. My computer doesn't have a dvd drive, so I am booting off of a flash drive with a bootable recovery CD image on it (I mistyped above when I references a recovery CD). 

gparted shows a single partition of 930GB. The drive is 1TB, so I think that some portion of the drive isn't being detected, even after after overhead and configuration settings, no?

On the other hand, your second command seems to yield different information: 

```
~$ sudo parted /dev/sda print all
Model: ATA ST1000LM014-1EJ1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size   File system  Name  Flags
 1      1049kB  538MB   537MB  fat32              boot
 2      538MB   794MB   256MB  ext2
 3      794MB   1000GB  999GB                     lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 17.1GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  17.1GB  17.1GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 982GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  982GB  982GB  ext4
```

---

### Post by ubfan1 on 2014-07-08
Disc size difference 930G vs 1T is probably just the result of using different units.  The marketing G is 10^^9, but the historical G was
2^^30.  The unit names are different, (gibi vs giga, etc). but that the first thing to think of when you find such a difference.

I have not heard of updates repartitioning the disk either.  I have seen a bug reported on the misleading words on the install media when it finds an Ubuntu install already present -- offering to "update or upgrade" without mentioning that the disk will be wiped also.
Was that what you did for your "update"?   

Updates on these new machines sometimes do some things I consider wrong, like deleting nvram boot entries, changing boot order, and updating bootloaders, but nothing on the order of repartitioning a disk.

---

### Post by yancek on 2014-07-08
Your output from parted shows that you have LVM (Logical Volume Managment) which takes up almost the entire drive, 999GB.  There is an option during installation to use LVM.  My understanding from reading other posts on the subject (never used it myself) is that it will overwrite everything.  I don't know how one would do this with an update.  You could try testdisk to recover data but not sure how that would work.

---

### Post by Peterlorre on 2014-07-09
Ah, I see. I did recently upgrade from 12.04 to 14.04, but I thought that I had gone into windows a few times after that (I may be mistaken).


I'd agree that that is seriously misleading language on the update if it neglects to mention a disk wipe. I guess it's time for me to reinstall.


Thanks again for all of your help on this.

---

### Post by oldfred on 2014-07-09
There is this bug on reinstall:
 Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

But the alternative installer with 12.04 clearly said LVM was a full drive install. New verbiage with 14.04 does not really say that.

But as in bug above since software does what it was designed to do, it is not a bug. And Ubuntu has never been good at fixing description issues as they do not consider it a bug.

---

