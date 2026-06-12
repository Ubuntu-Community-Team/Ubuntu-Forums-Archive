---
title: "gparted and ubuntu installation does not detect my hard correctly"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by I&amp;U on 2013-02-22
Hi all,
recently I've downloaded ubuntu 12.10 and I'm not able to install it because of I think 
a hard disk failure, ubuntu installation and G-Parted dont recognise my drives correctly and they just show my hdd as a raw one, (unallocated).
 I just have one hard (sda) and winxp is installed on that, 
disk utility on the ubuntu live recognises my hdd correctly,

This is what sudo sfdisk -l command shows me:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   6373    6374-  51199123+   7  HPFS/NTFS/exFAT
/dev/sda2       6374+  60801-  54428- 437186342+   f  W95 Ext'd (LBA)
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       6374+  19121   12748- 102398278+   7  HPFS/NTFS/exFAT
/dev/sda6      19122+  31221   12100-  97193218+   7  HPFS/NTFS/exFAT
/dev/sda7      31222+  43434   12213-  98100891    7  HPFS/NTFS/exFAT
/dev/sda8      43435+  60800   17366- 139492363+   7  HPFS/NTFS/exFAT

AND:

G-parted shows a warning too, (can't have a partition outside the disk!)
it takes a long time for g-parted to scan my devices when it starts, and at last it just shows an unallocated part with that warning  (can't have a partition outside the disk!).

thanks for any help

---

### Post by carl4926 on 2013-02-22
That's the strangest output I have seen...

What do you think is on those logical partitions?

---

### Post by dino99 on 2013-02-22
so you are using vista or w7 right ?
the first step is to check hdd settings inside the bios: how are they set ?

maybe the partition table needs to be rebuilt 

[http://askubuntu.com/questions/48717/how-to-manually-fix-a-partition-table](http://askubuntu.com/questions/48717/how-to-manually-fix-a-partition-table)

is your issue with the gparted found on 12.10 ?

---

### Post by I&amp;U on 2013-02-22
> **carl4926 said:**
> That's the strangest output I have seen...

What do you think is on those logical partitions?

thanks for your reply

they are just my drives with ntfs format, nothing else,
my last drive (sda8) is empty, and I want to allocate it for my ubuntu, but I couldn't do it,

---

### Post by carl4926 on 2013-02-22
> **I&U said:**
> thanks for your reply

they are just my drives with ntfs format, nothing else,
my last drive (sda8) is empty, and I want to allocate it for my ubuntu, but I couldn't do it,

Honestly it's not a pretty sight.
But obviously you need to format sda8.
But if Gparted isn't seeing the partitions, I think I agree that your partition table needs re-setting.

But tell us, if you go this route with the installer
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)

Do you see your partitions like this
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)
(ignore the text for now)

---

### Post by I&amp;U on 2013-02-22
> **carl4926 said:**
> Honestly it's not a pretty sight.
But obviously you need to format sda8.
But if Gparted isn't seeing the partitions, I think I agree that your partition table needs re-setting.

But tell us, if you go this route with the installer
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)

Do you see your partitions like this
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)
(ignore the text for now)

Yes I went there but as I said above it just shows me a raw hard disk named /dev/sda and with no partitions on it, and I just can make new partitions on it so this will cause data loss of course, 

I formatted sda8 with disk utility but didn't help.

---

### Post by carl4926 on 2013-02-22
So  
In windows, you can see the partitions? No errors reported?

Not sure what your best move is or at least how that can be done from windows ( I don't use it)

Perhaps @dino99 has idea

---

### Post by dino99 on 2013-02-22
how that hdd partitionned ? (extended, how many primary)

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by I&amp;U on 2013-02-22
> **dino99 said:**
> how that hdd partitionned ? (extended, how many primary)

one primary and extended part includes three drives and some unallocated part,
I used fdisk, as u mentiond before, to delete my last drive (sda8) which became the unparitioned part, and I created new partition there, but no result, still G-Parted and ubuntu installation dont detect my hard properly and my  hdd is still unallocated and raw with no drives, but correct in disk utility.

more:
I cant delete new partition from disk utility, when I do it it gives me this warning again:
(can't have a partition outside the disk!)

---

### Post by darkod on 2013-02-22
It obviously thinks there is a partition outside the disk, although according to sfdisk doesn't seem so.

You can try what parted shows from live mode, and also fixparts:
```
sudo parted -l
```

[www.rodsbooks.com/fixparts/](www.rodsbooks.com/fixparts/)

---

### Post by I&amp;U on 2013-02-22
> **darkod said:**
> It obviously thinks there is a partition outside the disk, although according to sfdisk doesn't seem so.

You can try what parted shows from live mode, and also fixparts:
```
sudo parted -l
```[www.rodsbooks.com/fixparts/]("http://www.rodsbooks.com/fixparts/")

sudo parted -l 
reported this:
Error: Can't have a partition outside the disk!                      

****** AND

sudo fixparts /dev/sda 
reported this:

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 976771055 sectors (465.8 GiB)
MBR disk identifier: 0x33043303
MBR partitions:

                                                                              Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *                     63    102398309   primary     Y        Y      0x07
   5             102398373    307194929   logical     Y        Y      0x07
   6             307194993    501581429   logical     Y               0x07
   7             501581493    697783274   logical     Y               0x07
   8             697785400    900000000   logical     Y        Y      0x83

---

### Post by jmore9 on 2013-02-22
You should try to download the gparted live cd and burn it to a cd and use that.  I use it all the time on windows and linux machines.

---

### Post by darkod on 2013-02-22
Sometimes all it needs is to rewrite the same table again. The fixparts output looks fine, if you select 'w' to write the table as it is, it should be fine.

But before doing that it's always a good advice to make a full backup of your system and data, just in case.

---

### Post by I&amp;U on 2013-02-22
> **darkod said:**
> Sometimes all it needs is to rewrite the same table again. The fixparts output looks fine, if you select 'w' to write the table as it is, it should be fine.

But before doing that it's always a good advice to make a full backup of your system and data, just in case.

thanks, really thank u
It worked ...

I rewrote the partition table on itself, 
now I can see my hdd with partitions corrctly as it is in the ubuntu installation.

---

### Post by carl4926 on 2013-02-22
> **I&U said:**
> thanks, really thank u
It worked ...

I rewrote the partition table on itself, 
now I can see my hdd with partitions corrctly as it is in the ubuntu installation.

Still looks like something the Dog dumped though :-)

Show us a screen of what you see in Gparted now

---

### Post by I&amp;U on 2013-02-22
> **carl4926 said:**
> Still looks like something the Dog dumped though :-)

Show us a screen of what you see in Gparted now

I took a screenshot of my ubuntu installlation page.
thanks again ;)

---

### Post by carl4926 on 2013-02-22
So maybe you plan to delete sda8 and then create:

swap 2GB or thereabouts
ext4 to use all the remainder for /

---

