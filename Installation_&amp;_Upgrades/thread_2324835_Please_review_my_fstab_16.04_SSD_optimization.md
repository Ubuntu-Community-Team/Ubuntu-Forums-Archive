---
title: "Please review my fstab: 16.04 SSD optimization"
date: 2016-05-16
forum: Installation &amp; Upgrades
---

### Post by m9ke2 on 2016-05-16
I would really appreciate some feedback on some changes I made to a copy of my fstab after installing 16.04.  What i am trying to do is: 1 - minimize writes to the SSD and 2 - enable trim. 

To make this easier to read, I added some white space between partitions, and labled where the partitions are with 
"#m9ke:  this is a partition on my ..."

Also moved swap off the SSD to the conventional HDD

One question for sure:  I am not sure what /boot/efi does.   It's on my SSD, but since I don't know what it's for, I did not add 'discard,noatime,nodiratime to it.  Should I do that?  Is it okay that it is vfat and not ext4?  What the heck is this partition for?  I am clueless as far as this one goes!

I would appreciate any feedback on the changes I made to the fstab, and some education about the /boot/efi partition!

Here is my fstab:

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


#m9ke: below is a partition on my SSD
# / was on /dev/sda2 during installation
UUID=50052078-a2ca-4f81-96d9-7fabcebddcd9 /               ext4 discard,noatime,nodiratime    errors=remount-ro 0       1


#m9ke: below is a partition on my SSD
# /boot/efi was on /dev/sda1 during installation
UUID=36C4-3FB7  /boot/efi       vfat    umask=0077      0       1




#m9ke: below is a partition on my conventional HDD
# /home was on /dev/sdb2 during installation
UUID=03c8d6fa-c35a-4f94-bbb4-1a62111ecacc /home           ext4    defaults        0       2


#m9ke: below is a partition on my conventional HDD
# swap was on /dev/sdb1 during installation
UUID=ddf1de77-ad81-4631-a6c7-33d46f0f5e99 none            swap    sw              0       0
```

---

### Post by ubfan1 on 2016-05-16
I think the noatime implies nodiratime, so having both is a little redundant.  The /boot/efi/... is the mount point for the UEFI EFI System Partition, which contains the bootloaders.  Not much is done with it, unless grub or shim get an update (rarely).  Not sure discard is the recommended way to run the TRIM these days, probably slows things down too much.  Running a cron job periodically I think was the latest recommended way.  The little I did with an SSD on Ubuntu, I just ran fstrim myself, but basically gave up on SSDs as trim wouldn't work over USB.

---

### Post by m9ke2 on 2016-05-16
Thanks ubfan1.  I will look into the latest posts on trim i can find. Also thanks for the education on /boot/efi/.  Much appreciated!

---

### Post by howefield on 2016-05-17
You'll probably find that Trim is enabled by default and will be run on a weekly cron if your SSD supports it.

```
more /etc/cron.weekly/fstrim
```

The only addition to the default settings I make for SSD is to add the following to the fstab.

```
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
```

---

### Post by oldfred on 2016-05-17
More info on ESP. It is the way new systems boot and can be seem somewhat like the old MBR or first sector of hard drive that BIOS boots from. But is larger and can support multiple booting where with MBR only one system can have boot code in MBR.

 ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)

Old BIOS system:

 BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS) 
 
UEFI normally uses gpt(GUID) partitioning and BIOS uses MBR(msdos)
 gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by m9ke2 on 2016-05-17
Thank you oldfred and howefield.   The education is much appreciated!

---

### Post by m9ke2 on 2016-05-17
howfield, I ran the command you suggested and got this back.  I am not sure how to interpret it.  can you comment?

```
m9ke@shadowbee:~/Desktop$ more /etc/cron.weekly/fstrim#!/bin/sh
# trim all mounted file systems which support it
/sbin/fstrim --all || true
m9ke@shadowbee:~/Desktop$ 
```

---

### Post by howefield on 2016-05-17
> **m9ke2 said:**
> howfield, I ran the command you suggested and got this back.  I am not sure how to interpret it.  can you comment?

Your output is just telling you that trim is set to run weekly on disks that support it.

To check whether your disk supports trim or not, you can run the following command..

```
sudo hdparm -I /dev/sda | grep "TRIM supported"
```

Do you know the make/model of your SSD ?

---

### Post by m9ke2 on 2016-05-17
thanks howefield.

My SSD is a Crucial BX-100. Firmware is latest.

Ran the command you suggested and got:

```
m9ke@shadowbee:~/Desktop$ sudo hdparm -I /dev/sda | grep "TRIM supported"
[sudo] password for m9ke: 
       *    Data Set Management TRIM supported (limit 8 blocks)
```

---

### Post by m9ke2 on 2016-05-17
I googled 'Data Set Management TRIM supported (limit 8 blocks)'.  It appears to mean my SSD supports trim, with the block limit being the max number of 512 byte blocks my SSD will handle from a single data set management command.

Further snooping on the net suggests  that trim via discard in the fstab is not recommended as much as scheduled trim these days.  And that scheduled trim was planned to be active by default after ubuntu 14.04.

If scheduled trim is active by default in my distro (16.04), and since my SSD supports trim, maybe I don't need any change to my fstab for trim.

Could someone confirm that given my version (16.04) and known trim support in my SSD I don't need to do anything else to have trim working?

---

### Post by howefield on 2016-05-17
I'm not sure that you need to worry about trim with a Crucial SSD, read up on Active Garbage Collection which is also supported by your disk.

[https://www.crucial.com/wcsstore/CrucialSAS/pdf/product-flyer/crucial-bx100-ssd-productflyer-en.pdf](https://www.crucial.com/wcsstore/CrucialSAS/pdf/product-flyer/crucial-bx100-ssd-productflyer-en.pdf)

---

### Post by m9ke2 on 2016-05-25
Thanks howefield!

For anyone who finds this thread i will summarize what i learned in figuring this out before marking this thread Solved.

Active garbage collection in Crucial branded drives is explained by Crucial on this page:
[http://forum.crucial.com/t5/Crucial-SSDs/My-SSD-used-to-be-so-much-faster-What-happened/ta-p/118310](http://forum.crucial.com/t5/Crucial-SSDs/My-SSD-used-to-be-so-much-faster-What-happened/ta-p/118310)

I don't think active garbage collection is a substitute for trimming in Crucial branded SSD drives.  In the above page, Crucial states that active garbage collection needs periods of inactive time (hours) to work.  They also give instructions to disconnect your SATA drive data cable, leaving the power connected to force active garbage collection.

So I poked around on the web and found that my SSD supports trim, and my linux distro (xubuntu 16.04)  has built-in support for trimming.  Consequently i did not make any changes to my system for trimming.

Two things I did do that are not related to trimming:
1.  added noatime to my fstab (reduces writes to the boot SSD)
2.  moved my swap partition off the boot SSD to a conventional spinning HD (again the goal is to reduce writes to the SSD)

Thanks again folks who participated in this thread!  Marking Solved.

---

### Post by howefield on 2016-05-26
Here's another point to think about, web browsers write a lot of data to the disk so it can be worth while putting the browser profile on the mechanical disk and pointing the web browser to it. If you have a goodly amount of memory you may find this more beneficial to your goal of minimising writes to the SSD than putting swap on the mechanical disk as swap may not even be ever used :)

---

