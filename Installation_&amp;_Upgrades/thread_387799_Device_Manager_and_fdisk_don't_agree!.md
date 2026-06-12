---
title: "Device Manager and fdisk don't agree!"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by Paploo on 2007-03-18
After monkeying around for a couple hours trying to get a windows drive installed in my machine along side my Ubuntu drive, I noticed something interesting in Device Manager.

For my main Linux partition (/dev/sdb1), it has the "volume.fstype" key set to "fat32" instead of ext3, the "volume.fsversion" key set to "FAT32", and the "volume.label" key denoted as a  box with 0007 in it instead of "Volume (ext3)".

However, fdisk, cfdisk, and parted all see /dev/sdb1 as ext3 and the OS boots and mounts the fs properly.

Is this something I should worry about and/or fix, or should I just let it be?  And if I do need/want to fix it, might how I do that?

I also noticed that cfdisk isn't seing /dev/sdb2, but fdisk and parted both are.  Should I be worried about that?

Note that I initially had my linux drive plugged into the SATA port that the windows drive was on when windows was installed, and so when windows boot it did *something* to the linux drive to cause it to become completely unmountable.  fsck, when ran, fixed a lot of stuff, and once fsck ran clean, I booted into linux and it ran just fine (and has been used all day without a single problem).

P.S. - Here is my fdisk -l output:

odin@odin-ubuntu:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9824    78911248+  83  Linux
/dev/sdb2            9825       10011     1502077+   5  Extended
/dev/sdb5            9825       10011     1502046   82  Linux swap / Solaris


P.P.S - Here is my parted output:

odin@odin-ubuntu:~$ sudo parted /dev/sdb
GNU Parted 1.7.1
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            

Disk /dev/sdb: 82.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  80.8GB  80.8GB  primary   ext3         boot 
 2      80.8GB  82.3GB  1538MB  extended                    
 5      80.8GB  82.3GB  1538MB  logical   linux-swap

---

