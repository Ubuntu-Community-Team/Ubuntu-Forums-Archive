---
title: "Re-Partitioning Problems - New Laptop"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by daka on 2008-08-30
Hi

New Toshiba L300 came with Vista. I still have a few (probably silly) reasons to keep the windows op sys. So I tried. Much drama, re-installing, now Vista doesn't boot. I am tempted to go all Linux!

One problem is that when I try to install XP it says that it can't find a hard drive and I can't install. Somehow the partitions now seem to be mounted on /dev/sda ! I thought I remember partitions mounted on hda not sda. Would Toshiba have done that or could I have accidentally done it somehow? (How do I reverse it if I did it accidentally) It looks like Toshiba and Microsoft set up a weird partitioning system off the bat, not permitting much manipulation without paying a price.

(I just checked my other laptop and it is set up as /dev/hda). How do I sort this problem out?... trying to..a) keeping Vista b) install XP c) clear the hard drive and start from scratch with Linux.

General advice appreciated

Here is some more info:

daka@daka-TB:~$ sudo fdisk -l
[sudo] password for daka:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4122adb

Device Boot Start End Blocks Id System
/dev/sda1 15494 30401 119748510 83 Linux
/dev/sda2 * 1 4017 32266521 7 HPFS/NTFS
/dev/sda3 4018 15372 91209037+ 5 Extended
/dev/sda4 15373 15493 971932+ 82 Linux swap / Solaris
/dev/sda5 14986 15372 3108546 82 Linux swap / Solaris
/dev/sda6 * 6030 14654 69280281 83 Linux
/dev/sda7 14655 14985 2658726 82 Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8589 MB, 8589934592 bytes
64 heads, 32 sectors/track, 8192 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x69737369

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot Start End Blocks Id System
/dev/sdb1 ? 912975 995343 84344761 69 Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb2 ? 830821 1743849 934940732+ 73 Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb3 ? 2 2 0 74 Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdb4 1409025 1409050 26207+ 0 Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
daka@daka-TB:~$

Looks like some Vista ended up on sdb1!! .... what now??

Daka

---

### Post by gatenby_jp on 2008-08-30
Bit difficult to advise you.

Your partition table looks a little screwed. 

There are two partitions sda3 and sda4 that I suspect are the Toshiba recovery partition and a diagnostics partition. 

the table should be sda1 hpfs/ntfs
sda2  usually dos 
sda3 ?
sda4 extended linux
thereafter your linux partitions
I cant visualise how this happened.

I think you had a dual layer DVD in the DVD drive and that is what sdb is about.
sda instead of hda is simply that the drive is sata instead of ide.

If you have media to re-install
Then start by re-installing XP / or Vista if you are a sucker for punishment.

When you get the option as to where you should install start by deleting all partitions ... then create a partition of 30 Gig format Ntfs ... and another of say 180 Gig format Ntfs leaving +/- 30 Gigs untouched ... now install your Windows on the first Partition of 30 gig. Now install your Linux on the unformatted portion of the hard disk ... however select manual formatting (create a 4th partition for swap) also mount /home on the second partition ... ie the big one formatted ntfs.

set the formatting as ntfs but not to format.

When you finish the Linux install you will have a directory in /home for the user name you created ... now create a directory My Documents within that /home/user directory

If you installed XP ... right click on My Documents and select properties ... then select move ... then navigate to the My Documents folder within D:\user\My Documents

I think the process is similar for Vista except you may need to do it for each Documents, Music, and Pictures.

This will result in My Documents being visible from either Linux or Windows.

Once you have completed and everything works from either System ... boot in Windows ... defragment your C: drive then with partimage create an image of the windows partition (sda1) save the image in /home/user you can now use partimage to recover your Windows should anything go wrong
with it.

As a rule of thumb it is recommended to keep you operating system and software to no more than about 30 Gigs ... I might be wrong about this but I have found that if Windows + Program files exceed this Windows becomes a real Dog to use.

---

### Post by caljohnsmith on 2008-08-30
When you repartitioned your HDD, did you use Vista's partitioning software or gparted in Ubuntu? If you used gparted, that will most likely make Vista unbootable since Vista maintains its own HDD partition table, and so it won't be correct with the new partitioning. Also, don't worry about the HDD being called "sda" instead of "hda", because Hardy calls just about every HDD sdX whether it is SATA or IDE. 

Also I noticed that on sda you have the boot flags set on two partitions. The boot flag should only be set on one partition on a HDD or you can run into problems. You can correct that with:
```
sudo fdisk /dev/sda
```
Then hit "a" to change a boot flag, and then enter "6" for partition 6 or sda6. That should hopefully remove that boot flag on sda6. Check it again with "sudo fdisk -l" to make sure. That could be the problem why the Windows XP installer doesn't like your HDD. Let me know how it goes or if you need more details/info.

---

