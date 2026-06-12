---
title: "correct alignment for 4096bytes disk - begginer"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by silvia_g on 2012-06-26
hey I've been using ubuntu for a couple of years now, but I am still an absolute begginer, please be kind..:)
I've bought a dell inspiron a month ago, and installed ubuntu 12.04 in a separate partition (since they made me pay for windows 7 I figured it was best to keep it there, in a small partition); then a week ago I started having huge problems, first during boot there were a lot of messages saying the disk had bad sectors, and now it doesn't boot at all;
googling and reading I think the problem is I have a disk divided in 4096 physical sectors and the table partition isn't aligned, so I'd like to reinstall everything from scratch with a propper alignment table, but I just can't manage to find instructions I'm able to understand; 
if someone could please share a comprehensive how-to for this situation, or direct me to some article where there's an explanation on how to proceed I'd much appreciate it;
also, I understand I should post the outcome of some command in order to provide accurate info on the problem I have, but don't know at one to use - just tell me what to do and I'll post it here!
thank you in advance, I hope someone will help me!
Silvia

/ ok so I-ve managed to boot from the cd, take pictures of disl utility and gparted outputs as well as fdisk l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x07f2837e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *      212992    41172991    20480000    7  HPFS/NTFS/exFAT
/dev/sda3        41172992   215252719    87039864    7  HPFS/NTFS/exFAT
/dev/sda4       215252990  1465147391   624947201    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       215252992   275253247    30000128   83  Linux
/dev/sda6       275255296   291254271     7999488   82  Linux swap / Solaris
/dev/sda7       291256320  1465147391   586945536   83  Linux

---

### Post by dino99 on 2012-06-26
several possible steps:

boot on windoz then do a chkdsk (or so)
boot on ubuntu, then into a terminal: sudo shutdown -R now

and if you does not really care about the Dell partition stuff, then format it :p

note: of course, each time you want to use a formatting tool, like gparted, its ALWAYS with unmounted partition.

---

### Post by oldfred on 2012-06-27
Your first partition starts at sector 63 which was the old way with XP. Vista changed to 2048 for better compatibility with newer drives. Linux/gparted changed but more recently to also use 2048 as the first sector.

You are showing a newer 4K drive
> Sector size (logical/physical): 512 bytes / 4096 bytes

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

But you cannot easily move Windows as the partition boot sector as to match the partition start and size. So any movement of the Windows partition corrupts the partition boot sector and requires repairs from a Windows repairCD or USB.

---

### Post by silvia_g on 2012-06-30
Ei finally, I formatted the pc and instaled ubuntu, working just fine now.
Thank you everybody for your help.

---

