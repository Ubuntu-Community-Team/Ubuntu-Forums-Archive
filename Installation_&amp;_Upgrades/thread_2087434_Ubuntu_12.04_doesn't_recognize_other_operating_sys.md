---
title: "Ubuntu 12.04 doesn't recognize other operating systems"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by pacman3000 on 2012-11-23
So, at first I must say that my problem is quite complex but I hope I am able to describe it clearly.

I used to have Ubuntu and Windows 7 installed and working pretty good together. Unfortunately, Windows was crashing on a regular basis and I wanted to repair it by extending Windows partition. One moment I got a bluescreen with partition program open and it made impossible to boot anything at all (>grub rescue and so on). I used Boot Repair with an Ubuntu LiveUSB, but now only Windows boots, with no sign of Ubuntu.

An attempt to install Ubuntu detects no operating system on the hard disk (neither working Windows or gone-somewhere Ubuntu) so I decided not to go any further with a reinstallation. After choosing 'Something else' as installation type, the installator offers nothing more than organizing a new partition table, without seeing the actual present one.

Now something on partition tabling, as I guess it's vital to the problem. Both fdisk and cfdisk refuse to say anything (obviously everything is run using a LiveUSB):

```
ubuntu@ubuntu:~$ sudo fdisk -l
fdisk: unable to seek on /dev/sda: Invalid argument
ubuntu@ubuntu:~$ sudo cfdisk

/* here appears, on an empty terminal screen:

                      FATAL ERROR: Cannot seek on disk drive
                            Press any key to exit cfdisk   /*


ubuntu@ubuntu:~$ 

```Fortunately, sfdisk and parted do say something (formatting added for the sake of better distinction of the two programs):

```
ubuntu@ubuntu:~$ sudo **sfdisk -l**

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *   1767+   6258-   4492-  36079228    7  HPFS/NTFS/exFAT
/dev/sda2       6258+  24075-  17817- 143114240    7  HPFS/NTFS/exFAT
/dev/sda3      29644+  30401-    757-   6076447+   5  Extended
/dev/sda4          0+   1766    1767-  14193396   83  Linux
/dev/sda5      29644+  30401-    757-   6076416   82  Linux swap / Solaris
/dev/sda6     291426+ 296994-   5569-  44725248   83  Linux

Disk /dev/sdb: 1023 cylinders, 119 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/101/37 (instead of 1023/119/62).
For this listing I'll assume that geometry.
Units = cylinders of 1913344 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      2+   2021-   2020-   3773088    c  W95 FAT32 (LBA)
        start: (c,h,s) expected (2,15,36) found (1,0,1)
        end: (c,h,s) expected (1023,100,37) found (935,100,37)
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
ubuntu@ubuntu:~$ sudo **parted**
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Error: Invalid argument during seek for read on /dev/sda                  
Retry/Ignore/Cancel? r                                                    
Error: Invalid argument during seek for read on /dev/sda                  
Retry/Ignore/Cancel? r                                                    
Error: Invalid argument during seek for read on /dev/sda                  
Retry/Ignore/Cancel? i                                                    
Error: Invalid partition table on /dev/sda -- wrong signature 2c6b.       
Ignore/Cancel? i                                                          
Model: ATA Hitachi HTS72322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 4      32.3kB  14.5GB  14.5GB  primary   ext4
 1      14.5GB  51.5GB  36.9GB  primary   ntfs            boot
 2      51.5GB  198GB   147GB   primary   ntfs
 3      244GB   250GB   6222MB  extended
 5      244GB   250GB   6222MB  logical   linux-swap(v1)

(parted) quit                                                             
ubuntu@ubuntu:~$ 
```Partition /dev/sda6 seems to be the odd one - but interesingly, its data could be read on Windows using ext2Read (but not other similar programs).

So I think that's it. Is there any hope of running previous Ubuntu installation, or at least reinstalling it without need to repartition the whole disk (and therefore reinstalling Windows as well)?

---

### Post by darkod on 2012-11-23
Fixparts should be able to sort out that error:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

And I wouldn't try reading linux partition from windows, that might be the reason why this happened.

---

