---
title: "install ubuntu without changing MBR"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by arjunajay on 2012-01-11
I have a laptop that seems to have recovery, windows7, and some other strange partitions. Is it possible to install Ubuntu or  Linux for that matter on a logical drive, **but at the end of the installation tell it to write the MBR/GRUB to a USB stick and NOT to the primary partition?**
This is so that during power up, i can use the USB to bring up a GRUB menu (and nothing more) and then have it load Linux from harddrive as if nothing has happened.

The current mbr has many options including bringing up a 'direct to web' option which opens a browser without going to windows and other strange options like recovery, backup etc. I don't want to risk losing any such thing.

---

### Post by BC59 on 2012-01-11
Try to see here if there is something to help:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Mark Phelps on 2012-01-11
> **arjunajay said:**
> I have a laptop that seems to have recovery, windows7, and some other strange partitions.

STOP -- before you do major damage!

Many laptops come with the maximum of 4 Primary partitions already configured to the hard drive.  If you force the creation of a fifth, you will force conversion of your Windows "Basic Volumes" into "Dynamic Disks" -- something you do NOT want to do!

Boot into an Ubuntu desktop CD, select Try Ubuntu, and when you get to a desktop, open a Terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out all the partitions on your drive.  Post that information back here.

---

### Post by ottosykora on 2012-01-11
>The current mbr has many options including bringing up a 'direct to web' option which opens a browser without going to windows<

just curious: is this a UEFI computer where all those functions are provided by the bios in fact?

---

### Post by arjunajay on 2012-01-12
> **Mark Phelps said:**
> STOP -- before you do major damage!
OOPS! I may already have :-\"
It came with some partitions. but since they were few in number(only C:&D: it seems) and NTFS, I used windows partition manager to split into several of which two were made FAT so  that in future I would be able to share data b/w windows and Linux. This was several months back.  only now have I downloaded and burnt the Linux CD (lazy me). is it still possible to undo the 'dynamic_ness' that you mentioned?

> **Mark Phelps said:**
> 
Many laptops come with the maximum of 4 Primary partitions already configured to the hard drive.  If you force the creation of a fifth, you will force conversion of your Windows "Basic Volumes" into "Dynamic Disks" -- something you do NOT want to do!

Boot into an Ubuntu desktop CD, select Try Ubuntu, and when you get to a desktop, open a Terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out all the partitions on your drive.  Post that information back here.
will post it. my laptop is hiccuping when i live boot Ubuntu. have to stick with Lubuntu or Xubuntu probably.

>  is this a UEFI computer where all those functions are provided by the bios in fact?
probably not. i'm not sure. its a sony vaio eb46. didn't have any  option to install xp and linux which i would have preferred. :(

---

### Post by Mark Phelps on 2012-01-12
OUCH!!  Since you apparently already have the Dynamic Disk mess, there may be no way to undo that without data loss.  I had done some searches on this, but the links I found dealt with empty Dyamic Disks.

I did find the one link below -- but to implement this, you need access to Windows 2000 tools:

[http://www.petri.co.il/forums/showthread.php?t=3844]("http://www.petri.co.il/forums/showthread.php?t=3844")

---

### Post by ottosykora on 2012-01-12
I just thought that you mentioned that your "MBR" provides thigs like web access etc, well mbr does not do such things, but in recent computers there is this new bios included which has such capabilities, it can connect to net etc.
So to me it just looks like you have something like that. In which case the whole install is getting different.

So check what exact type of partitions you have, see if you have basic or dynamic first.

---

### Post by arjunajay on 2012-01-12
> **Mark Phelps said:**
> OUCH!!  Since you apparently already have the Dynamic Disk mess, there may be no way to undo that without data loss.  I had done some searches on this, but the links I found dealt with empty Dyamic Disks.

I did find the one link below -- but to implement this, you need access to Windows 2000 tools:

[http://www.petri.co.il/forums/showthread.php?t=3844]("http://www.petri.co.il/forums/showthread.php?t=3844")

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa9f9f7b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    28311551    14154752   27  Hidden NTFS WinRE
/dev/sda2   *    28311552    28516351      102400    7  HPFS/NTFS/exFAT
/dev/sda3        28516352   149518335    60500992    7  HPFS/NTFS/exFAT
/dev/sda4       149518336   976771071   413626368    f  W95 Ext'd (LBA)
/dev/sda5       149520384   354320383   102400000    7  HPFS/NTFS/exFAT
/dev/sda6       354322432   567171071   106424320    7  HPFS/NTFS/exFAT
/dev/sda7       567173120   771993599   102410240    7  HPFS/NTFS/exFAT
/dev/sda8       771995648   812974079    20489216    b  W95 FAT32
/dev/sda9       812976128   976771071    81897472    7  HPFS/NTFS/exFAT


```

---

### Post by Mark Phelps on 2012-01-12
OK ... so it looks like you have three Primary partitions and one Extended partition -- with a bunch of other partitions inside.

But, I'm confused about your "dynamic" comment because, when Windows converts NTFS volumes to Dynamic Disks, the Linux fdisk result generally shows those partitions as SFS, not NTFS.

---

### Post by ottosykora on 2012-01-13
I noticed, that when using the windows tool, had 2 partitions, added 3, it produced auomatically an extended and placed the new one inside it.
So first it looked as if it was creating 2+3, but it did not.

---

### Post by varunendra on 2012-01-13
> **Mark Phelps said:**
> But, I'm confused about your "dynamic"  comment because, when Windows converts NTFS volumes to Dynamic Disks,  the Linux fdisk result generally shows those partitions as SFS, not  NTFS. I don't have in-depth knowledge about dynamic disks, but I  believe windows makes that conversion only when the existing number of  primary partitions is already 4 and more partitions are needed to be  added. It seems like OP had less than 4 primary partitions at the time he created more, and thus windows did what it does by default - created an extended partition (which is good for his current requirement), not dynamic ones.

> **arjunajay said:**
> **..****at the end of the installation tell it to write the MBR/GRUB to a USB stick and NOT to the primary partition?**.
Yes, it is possible and perfectly ok to install Ubuntu in an extended partition and put Grub in a USB drive. You can do this by choosing advance partitioning mode (Listed as "Something else" option in the partitioning stage of installation.) Be careful while choosing the partition to install Ubuntu upon.

Just select an empty extended partition for Ubuntu, and for grub, select the USB drive (under "Device for bootloader installation.."). It should be /dev/sdb for your laptop (if it is the only drive attached other than the internal HDD).

> **arjunajay said:**
> ...of which two were made FAT so  that in future I would be able to share data b/w windows and Linux..
Ubuntu can 'see' and use NTFS partitions, so it doesn't need to be FAT/32 to share data between two.

---

