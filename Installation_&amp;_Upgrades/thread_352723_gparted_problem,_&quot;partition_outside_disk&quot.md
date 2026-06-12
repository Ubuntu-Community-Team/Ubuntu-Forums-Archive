---
title: "gparted problem, &quot;partition outside disk&quot;"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by jbrinchmann on 2007-02-03
Hi folks,

I have been using Mandriva for a long time but had decided to move to Ubuntu but have hit a snag upon starting install.

My problem is with my primary hard drive, which is a ~120 Gb ATA drive with a few partitions, a primary for Windows, & one for Linux. The latter has a few logical drives which previously were / /swap /usr & /home. It works ok from the Live CD - mount works, fdisk works fine etc.

When I try to install Ubuntu it wants to sort out my partitions but can't understand my primary disk..., basically what happens is that gparted barfs as show below with a "Can't have a partition outside the disk!". I presume there is something odd with my partition table.... I can of course reformat everything & on the Linux side that is not a big deal but I really really didn't want to reinstall Windows. Does anyone have any ideas about this problem, is it fixable/can I go around it in any way?

My fdisk -l output is:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100       14594    76268587+   f  W95 Ext'd (LBA)
/dev/hda5            5100        5200      811251   83  Linux
/dev/hda6            5201        5582     3068383+  82  Linux swap / Solaris
/dev/hda7            5583        6091     4088511   83  Linux
/dev/hda8            6092       14594    68294835   83  Linux

and running parted is not terribly informative:

ubuntu@ubuntu:~$ sudo parted /dev/hda
GNU Parted 1.7.1
Using /dev/hda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Error: Can't have a partition outside the disk!                           


Any ideas?

                               Cheers,
                                      Jarle.

---

### Post by housam on 2007-02-04
I see from your fdisk -l table that your HDD has 14593 cylinders, but hda2 , the extended partition boundry is up to 14594 cylinders ( also appears in hda8 the last partition )which means that it is out of the drive volume and you have to edit the partition table to fix it.

First print in a paper the result of fdisk -l table . you will need it to rewrite the table again .

In a terminal type :
```
fdisk /dev/hda
```

then type : p to list the partition table
then delete the extended partition hda2 by typing  : d and go for it.
then rewrite it by typing n for new partition and asign it as : e for extended then writ the number of cylinders 5100 at the begining and 14593 at the end . then type : t to give it its code.
And do the same for hda8

**READ** [THIS GUIDE ]("http://community.linux.com/howtos/Partition/fdisk_partitioning.shtml")CAREFULLY BEFORE DOING THE EDIT. specially parts 5 & 8

---

### Post by jbrinchmann on 2007-02-04
Thank you housam,

That did the trick - I still needed to reformat my Linux side disks because the end result was a warning that the the superblock on /dev/hda8 gave a different size from the physical size of the disk (possibly due to a mistake on my part). 

No matter, I had backed up everything and anyway my home directory (on /dev/hda8) used to be ext2 so now I had a good reason to switch to ext3 :) 

Thanks again!

            Jarle.
:KS

---

### Post by earthmeLon on 2008-04-18
Thanks!!! This helped a bunch.

Only thing is my problem wasn't on my extended partition, it was on a logical one.  Now I just have to figure out how to recover to data on there :P

---

