---
title: "Maximum number of partitions"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by ryukocn on 2007-05-16
I am trying to install ubuntu 7.0.4 in my laptop, everything seems good at the beginning. I use alternative disk because desktop disk doesn't work in my laptop. I don't know why. 
Anyway, it should be fine if the alternative disk works. 
But i encounter another question, I want to install it into a new partition , but the partitioner says the blank area is not usable, is there a maximum number limitation there?

---

### Post by mpvano on 2007-05-16
The IBM PC uses a partitioning scheme that only allows 4 "primary" partitions. This limit cannot be changed.

A work around was developed by IBM and Microsoft early on in the history of the machine. That workaround used ONE of the four partitions as an "extended" partition which is a container for a large number of additional partitions These partitions can be used for many things, but are not usually usable for direct booting without some very elaborate tricks.

I believe (can't remember right now) up to 255 partitions in the "extended" container are possible, but few things can make use of more than 8 or so.

Before you can make any extended partitions, you need to make the container partition for them and it must be large enough to hold all of them.

In most linux distributions, "primary" partitions are numbered 1-4 and 5-255 are partitions in the "extended" container.

I believe most distributions now try to avoid making "primary" partitions except for the one used to boot - typically the /boot or / partition if /boot is part of it. This strategy preserves the primary partitions for use with additional operating systems that need to install boot loaders directly.

There are many other "rules" some operating systems like Windows variants have for using partitions, so you may find that surprising things happen if you make more than one primary partition of a given type. Most partitioning utilities enforce some basic rules about things like this automatically.

The most important restriction for most Ubuntu users is that very few BIOS roms allow booting directly from a partition in the "extended" container and to be started by the BIOS a boot loader must be in a partition on the first disk. Grub must be installed in a primary partition to be "activated" and booted directly by the BIOS as the first stage loader.

Other ways to use Grub and other loaders) involve "chain" loading, where the primary loader (Grub or another fancy loader that knows how to "chain-load") runs when the machine starts and then transfers control to a second boot loader (like another complete grub installation) on a partition on another disk or in an extended partition.

For most future flexibility, t's best to try to only use one "primary" partition for linux if you are partitioning manually - if you need more, even a swap partition, you should make an extended partition and create the rest in there. Ubuntu's partitioners often use this strategy for the swap and other partitions in a multipartition install.

A common situation you see today is that two primary partitions (often hda1 and hda2) are used by the original XP installation, and by a "recovery" or "service" partition installed by the machine manufacturer. This only leaves two more primary partitions. Resizing the original partitions allows room to make a single primary partition for a new operating system's bootable partition (often hda3), and the fourth primary partition is used to make an extended partition (in this example, hda4) to contain any others needed for swap, et cetera, which end up with numbers starting with hda5.

Hope this information gets you started, but the subject is a complicated one with many subtleties (especially if you have an older machine or one of the OS installations is an antique) . The complete GRUB manual has a lot of information on the subject, but it's not easy reading....

Mario

---

### Post by ryukocn on 2007-05-16
Thank you for instant response.
Well, your explanation is very clear and detail. As you mentioned, I got a little complicated situsation here.

I am sure this laptop has no pre-installed stuff or hidden partition on it, but I have been used it for experiences, as a result, many kinds of OSs have been installed.

I got a MS OS Loader on hd0,0 and hd0,4~hd0,7 are Windows NTFS
here is the screen information where i was stopped, and the OSs information is added by me. 
hd0,0  Windows 2000 primary (2.1G)
hd0,4  Windows XP logical (4.2G)
hd0,5  Windows XP logical (4.2G)
hd0,6  Windows XP logical (4.2G)
hd0,7  Windows XP logical (4.2G)
hd0,8  Swap logical (312.5M)
hd0,2  Debian 3.1r2 logical  (12.6G)
hd0,3  Debian 4.0r0 primary (12.0G)
hd0,9  Ubuntu 6.1.0 primary (12.0G)
unused unusable (24.2G)

Do you think I can make a new Ubuntu 7.0.4 installation on the unused partition? 

Thank again.

---

### Post by bulldog on 2007-05-16
Well you have 3 primary's and 5 logicals so far so good.
The question is,where is the extended partition?
Is the free space inside or outside the extended partition?
If it is outside the extended partition you have to try to resize the extended and add the free space to it.
Then you can make logical partitions from the free space.

But it's a little complicated,because it's rather important where the free space is on the hdd.
If it is right between two primary's it will be hard to add it to the extended partition.

---

### Post by eyemean on 2007-05-16
Hi

I've recently got into using Ubuntu but still using windows xp therefore dual booting.
When i installed Ubuntu (approx 6th time due to me messing up ubuntu somehow, lol) I had assumed that all drives should be Primary.  I had no there was a limit of 4 Primarys per drive.

As you can see below i have 4 primary paritions and 28 Gig of unallocated space which i wanted to convert to FAT32 so i could transfer files between both systems with out any risk of corruption.

Im wondering if there is anyway to change the "Linux swap" and 2nd "Linux Ext3" to logical partitions? 

(25 Gig) - Windows - NTFS - Primary 
(15Gig) - Linux Ext3 - Primary
(1 Gig) - Linux Swap - Primary 
(9 Gig) - Linux Ext3 - Primary 
(28 Gig) - Unallocated - Primary

I would really appreciate anyone's help here as I don't want to go through installing Ubuntu again.

Thank you in advance.
Regards
Eyemean

---

### Post by ricrac on 2007-05-17
eyemean asks;
Im wondering if there is anyway to change the "Linux swap" and 2nd "Linux Ext3" to logical partitions?
(25 Gig) - Windows - NTFS - Primary
(15Gig) - Linux Ext3 - Primary
(1 Gig) - Linux Swap - Primary
(9 Gig) - Linux Ext3 - Primary

(28 Gig) - Unallocated - Primary  <- wrong, not primary, not allocated anywhere
(28 Gig) - Unallocated 

Yes, but it's a little complicated and easy to shoot yourself in the foot if you don't pay attention.
In short, for a "safe" clean way to do it, you'll need to clear the 9gb primary partition 4.  If this is just data no problem, if it's /usr or some other mountpoint used in the system it will be more complicated.
Let's consider the case that the 9gb primary partition #4 contains data and you have free space on 25gb or 15gb temporarily.

This can all be done from any Ubuntu, Knoppix or other LiveCD.
Boot onto livecd mount partition 2 and 4, 15gb and 9gb. Copy all data from 4 to 2.
Run fdisk. 
Delete partition 4
Delete partition 3
Create Partition 3, type extended
Create logical partition 5, size 1gb, type swap
Create logical partition 6, size 9gb, type ext3
Create logical partition 7, size 28gb, type ext3

Fat32 for transfer.
Are people having problems with Fuse and ntfs-3g?  I have yet to have corruption. I copy mostly large files between systems.  I would be leary if I had any linux stability issues or power fluctuation issues, otherwise I use ntfs-3g on a daily basis and it hasn't failed me yet.
Note, I use XP not Vista.  I don't know if there are any issues with Vista and ntfs-3g. 

XP is unsecure enough.  I would not recommend anyone using fat32 vs. ntfs, except on external devices which I would still use as fat32.  Additionally, I use files larger than 4gb which won't work on Fat32.

---

### Post by ryukocn on 2007-05-17
> **bulldog said:**
> Well you have 3 primary's and 5 logicals so far so good.
The question is,where is the extended partition?
Is the free space inside or outside the extended partition?
If it is outside the extended partition you have to try to resize the extended and add the free space to it.
Then you can make logical partitions from the free space.

But it's a little complicated,because it's rather important where the free space is on the hdd.
If it is right between two primary's it will be hard to add it to the extended partition.

I am not sure about the layout of the partitions but I can imagine the free space is outside the extended partition. 

I guess it should be OK to install new Ubuntu into a new logical partition, couldn't I just create a new logical partition for the new installation if there is a limitation of 3/4 primary partition?

Here is my fdisk output if it can help you locate my problem

[COLOR="Blue"]
Command (m for help): p

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         255     2048256    7  HPFS/NTFS
/dev/hda2             256        3868    29021422+   f  W95 Ext'd (LBA)
/dev/hda3            3869        5327    11719417+  83  Linux
/dev/hda4   *        5328        6786    11719417+  83  Linux
/dev/hda5             256         765     4096543+   7  HPFS/NTFS
/dev/hda6             766        1275     4096543+   7  HPFS/NTFS
/dev/hda7            1276        1785     4096543+   7  HPFS/NTFS
/dev/hda8            1786        2295     4096543+   7  HPFS/NTFS
/dev/hda9            2296        2333      305203+  82  Linux swap / Solaris
/dev/hda10           2334        3868    12329856   83  Linux

Command (m for help): n
No free sectors available

Command (m for help):

[/COLOR]

I need help to create a new partition. any suggestion?

Thanks in advance.

---

### Post by kelvin spratt on 2007-05-17
i also cannot see the point of Fat32 its backwards technology, i duel boot and store everything in ntfs we no problems, i think its more a problem of (teaching old dogs new tricks) like the command line lots of things can now be done graphically but people try to force the command line unto newbies and that puts them of in a lot of cases

---

### Post by ricrac on 2007-05-17
ryukocn,

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 1 255 2048256 7 HPFS/NTFS
/dev/hda2 256 3868 29021422+ f W95 Ext'd (LBA)
/dev/hda3 3869 5327 11719417+ 83 Linux
/dev/hda4 * 5328 6786 11719417+ 83 Linux
/dev/hda5 256 765 4096543+ 7 HPFS/NTFS
/dev/hda6 766 1275 4096543+ 7 HPFS/NTFS
/dev/hda7 1276 1785 4096543+ 7 HPFS/NTFS
/dev/hda8 1786 2295 4096543+ 7 HPFS/NTFS
/dev/hda9 2296 2333 305203+ 82 Linux swap / Solaris
/dev/hda10 2334 3868 12329856 83 Linux

Command (m for help): n
No free sectors available

Partitions were created "out of order", this should work, but sometimes doesn't. 
...Start End Blocks should count up for primaries and extended
...Primaries should come before extended
...Logical Start End Blocks should count up, 1st logical starting at the start of the Extended and last logical ending at the end of extended
...Normally you would use fdisk, eXpert mode, Fix partition order, to fix a partition table with out-of-order ids, but in this case the partitions themselves are out-of-order.

Create partitions in "correct" order to avoid confusion.

Again, except for a few programs, this layout will function and you could install into primary partitions 3 or 4, or extended partition 10 as is, given you have space available on those partitions or format and overwrite.

The problem is your extended partition does not use the "rest" of the drive, and primary have been created after the extended blocking further expansion.  

The easiest fix is dd to an external HD or dd over ssh partitions 3 and 4. 
hd0,2 Debian 3.1r2 logical (12.6G)
hd0,3 Debian 4.0r0 primary (12.0G)
Then extend the logical partition to cylinder 9733, the end of the disk.
/dev/hda2 256 9733 29021422+ f W95 Ext'd (LBA)
Then use fdisk and fix the partition id order
Then create logical partitions and restore the two partitions into logical partitions.  Booting from extended partitions is fine for linux (not windows), but you'll need to change fstab, etc. to match partition id changes.

If you want 3 primaries, you'll need to backup the whole drive, delete all partitions except the first, create partition 2 and 3 as 12gb primaries, then partition 4 as extended for the rest of the disk.  You'll still be changing at least one fstab from hda4 to hda2, you can restore hda3 to the new hda3.  The windows drives are probably just "data" drives and the change in partition id should be auto detected/corrected.  You may need to run disk administrator to remap drive letters.

---

### Post by bulldog on 2007-05-17
> **eyemean said:**
> Hi

I've recently got into using Ubuntu but still using windows xp therefore dual booting.
When i installed Ubuntu (approx 6th time due to me messing up ubuntu somehow, lol) I had assumed that all drives should be Primary.  I had no there was a limit of 4 Primarys per drive.

As you can see below i have 4 primary paritions and 28 Gig of unallocated space which i wanted to convert to FAT32 so i could transfer files between both systems with out any risk of corruption.

Im wondering if there is anyway to change the "Linux swap" and 2nd "Linux Ext3" to logical partitions? 

(25 Gig) - Windows - NTFS - Primary 
(15Gig) - Linux Ext3 - Primary
(1 Gig) - Linux Swap - Primary 
(9 Gig) - Linux Ext3 - Primary 
(28 Gig) - Unallocated - Primary

I would really appreciate anyone's help here as I don't want to go through installing Ubuntu again.

Thank you in advance.
Regards
Eyemean

In your case it's best to delete the swap partition [primary] then you'll have 29GB unused space.
Make an extended partition 29GB and create the swap as a logical and the other 28GB can you use too for one or more logical partitions.
You have to edit the fstab file to point it to the new swap file partition because the old one doesn't exist anymore.

---

### Post by ricrac on 2007-05-17
eyemean,
bulldog's fix is easier, faster and will work fine.

I personally don't like to build partitions out of order because of confusion and potential for  problems like ryukocn's issue.

---

### Post by eyemean on 2007-05-17
Thanx for everyones help, in the end i kind of messed it up when I tried to sort it out,lol.
Nevermind, i just reinstalled Ubuntu and this time partitioned the drives correctly.

Thanx again much appreciated.

---

### Post by eyemean on 2007-05-17
Thanx for every ones help it was much appreciated.

But stupid me managed to mess it up when i was trying to sort out the partitions so just ended up reinstalling Ubuntu.  Luckily i didnt really have many docs in Ubuntu so was painless.

Reinstalled and this time partitioned everything correctly.

thanx again.

- Sorry for double posting, net cut off and i didnt realise 1st post went through.
If a mod can delete this one that would be great.

---

### Post by ryukocn on 2007-05-20
> **ricrac said:**
> ryukocn,

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 1 255 2048256 7 HPFS/NTFS
/dev/hda2 256 3868 29021422+ f W95 Ext'd (LBA)
/dev/hda3 3869 5327 11719417+ 83 Linux
/dev/hda4 * 5328 6786 11719417+ 83 Linux
/dev/hda5 256 765 4096543+ 7 HPFS/NTFS
/dev/hda6 766 1275 4096543+ 7 HPFS/NTFS
/dev/hda7 1276 1785 4096543+ 7 HPFS/NTFS
/dev/hda8 1786 2295 4096543+ 7 HPFS/NTFS
/dev/hda9 2296 2333 305203+ 82 Linux swap / Solaris
/dev/hda10 2334 3868 12329856 83 Linux

Command (m for help): n
No free sectors available

Partitions were created "out of order", this should work, but sometimes doesn't. 
...Start End Blocks should count up for primaries and extended
...Primaries should come before extended
...Logical Start End Blocks should count up, 1st logical starting at the start of the Extended and last logical ending at the end of extended
...Normally you would use fdisk, eXpert mode, Fix partition order, to fix a partition table with out-of-order ids, but in this case the partitions themselves are out-of-order.

Create partitions in "correct" order to avoid confusion.

Again, except for a few programs, this layout will function and you could install into primary partitions 3 or 4, or extended partition 10 as is, given you have space available on those partitions or format and overwrite.

The problem is your extended partition does not use the "rest" of the drive, and primary have been created after the extended blocking further expansion.  

The easiest fix is dd to an external HD or dd over ssh partitions 3 and 4. 
hd0,2 Debian 3.1r2 logical (12.6G)
hd0,3 Debian 4.0r0 primary (12.0G)
Then extend the logical partition to cylinder 9733, the end of the disk.
/dev/hda2 256 9733 29021422+ f W95 Ext'd (LBA)
Then use fdisk and fix the partition id order
Then create logical partitions and restore the two partitions into logical partitions.  Booting from extended partitions is fine for linux (not windows), but you'll need to change fstab, etc. to match partition id changes.

If you want 3 primaries, you'll need to backup the whole drive, delete all partitions except the first, create partition 2 and 3 as 12gb primaries, then partition 4 as extended for the rest of the disk.  You'll still be changing at least one fstab from hda4 to hda2, you can restore hda3 to the new hda3.  The windows drives are probably just "data" drives and the change in partition id should be auto detected/corrected.  You may need to run disk administrator to remap drive letters.

ricrac, 

Thank you very much. I have sucessfully installed Ubuntu in my laptop just as you told me. 
;)

---

