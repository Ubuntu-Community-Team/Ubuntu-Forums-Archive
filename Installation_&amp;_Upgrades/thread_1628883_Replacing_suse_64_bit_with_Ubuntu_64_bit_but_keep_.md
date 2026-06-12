---
title: "Replacing suse 64 bit with Ubuntu 64 bit but keep win 7"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by ciprianni on 2010-11-23
Hi there guys. I am new on this forum so please don't be mean to me. :)  I have an Acer aspire 5739G currently running dual boot: openSuse 64 bit and win 7 64Bit. I need some advice because I am no linux expert. This are my problems/questions:

1. I would like to get rid of openSuse and install Ubuntu 64 bit.
2. Is it possible to install Ubuntu but using the same partitions from openSuse?
3. I can not afford to repartition the hard drive and delete all my information because I have college projects to complete and windows is crucial for this.
4. After installing Ubuntu, I would like to have a running dual boot between Ubuntu and Win 7.
5. After reading all of the above and if its possible to install Ubuntu over Suse, what is the best installation procedure to follow?

Conclusion: I would like to replace Suse with Ubuntu 64bit without repartitioning the hard drive or touching win 7. At the same time I would like to keep the dual boot working between Ubuntu and Win 7.

Thanks for all your time reading this and any help will be appreciated.
Ciprianni

---

### Post by lmarmisa on 2010-11-23
I believe that this is possible.

During the installation of Ubuntu you should select the manual option for defining the partitions and then select the format option for the Ubuntu root partition. Not too difficult, at all.

It would be nice to know how your partitions are defined. Please, post the output of this command (or the equivalent command in openSuSe):

```

sudo fdisk -l

```

---

### Post by Mark Phelps on 2010-11-23
Since you'4re dual-booting with Win7, if you haven't already done this (and most have NOT), boot into Win7, run the Backup feature, and create and burn a Win7 Repair CD.  This will come in handy later if you need to repair the Win7 Boot Loader during dual-boot reload.

---

### Post by nothingspecial on 2010-11-23
First, back up all your college work and other stuff  before installing anything. Things can go wrong.

Boot the ubuntu live cd/usb

Choose install.

When you get to the partitioning bit choose manual/advanced

Select the partition with the linux file system, I don`t know what suse uses (ext3/ext4?)

Choose to use it as an ext4 journalling file system.

Select a mount point of /

Check/tick the format box.

Do not go anywhere near the windows partition.

Review what you have done.

Check it again.

Install.

This will completely nuke suse and any data you have within it.

---

### Post by kansasnoob on 2010-11-23
> **ciprianni said:**
> Hi there guys. I am new on this forum so please don't be mean to me. :)  I have an Acer aspire 5739G currently running dual boot: openSuse 64 bit and win 7 64Bit. I need some advice because I am no linux expert. This are my problems/questions:

1. I would like to get rid of openSuse and install Ubuntu 64 bit.
2. Is it possible to install Ubuntu but using the same partitions from openSuse?
3. I can not afford to repartition the hard drive and delete all my information because I have college projects to complete and windows is crucial for this.
4. After installing Ubuntu, I would like to have a running dual boot between Ubuntu and Win 7.
5. After reading all of the above and if its possible to install Ubuntu over Suse, what is the best installation procedure to follow?

Conclusion: I would like to replace Suse with Ubuntu 64bit without repartitioning the hard drive or touching win 7. At the same time I would like to keep the dual boot working between Ubuntu and Win 7.

Thanks for all your time reading this and any help will be appreciated.
Ciprianni

You didn't mention which version of Ubuntu you'll be installing but the installer has been redesigned in 10.10 (Maverick) so most older guides might confuse you. I compiled some info regarding the new installer:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

It would be best for us to see the output of:

```
sudo fdisk -l
```

Run from the Ubuntu Live CD so we can properly identify the openSuse partitions.

---

### Post by ciprianni on 2010-11-23
Thanks guys for all the info. The version I am going to install is Ubuntu 10.10 64bit. The code gave me this output:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc6403338

   Device Boot           Start             End            Blocks        Id        System
/dev/sda1           1                 13        102400          7         HPFS/NTFS

Partition 1 does not end on cylinder boundary.

/dev/sda2                       13               6622        53082112   7         HPFS/NTFS
/dev/sda3    *            6622     60802      435201024     f         W95 Ext'd (LBA)
/dev/sda5                  6622             6885          2109440      82        Linux swap / Solaris
/dev/sda6                   6885             9495         20971520     83        Linux
/dev/sda7                   9496            13151       29358080     83       Linux
/dev/sda8                13151            60802    382757888      7      HPFS/NTFS

I am going to attempt the installation after I'm going to complete some projects. Not sure when this will be but in the mean time I want to gather as much info as possible so the installation will go smooth.

Regards,
Ciprianni

---

