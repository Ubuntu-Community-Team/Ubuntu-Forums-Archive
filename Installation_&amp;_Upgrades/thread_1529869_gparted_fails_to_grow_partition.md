---
title: "gparted fails to grow partition"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by captainentropy on 2010-07-12
Hi everyone,
 
So, I have a machine running Ubuntu Server 9.10 installed on an 80GB RAID1 disk. The system has two arrays (one data, the other backup), each of the same size in RAID6 with ext4 fs, connected to separate 3ware 9690 controller cards. I had to increase the size of the arrays from 8TB to 12TB. No problems - added the drives, migrated the new disks into the array, rebooted the server, and everything is visible. I unmounted the drives and then attempted to grow the partition (it's a single partition), starting with the backup array, using gparted. It sees the unallocated space but when I try to grow the partition into the unallocated space it fails. Here's the gparted error details:
 
> 
[FONT=Times New Roman][FONT=Times New Roman]GParted 0.4.5[/FONT]
[FONT=Times New Roman]Libparted 1.8.8.1.159-1e0e[/FONT]
**[FONT=Times New Roman]Grow /dev/sdc1 from 7.28 TiB to 10.91 TiB[/FONT]**[FONT=Times New Roman] 00:13:24 ( ERROR ) [/FONT]
 
[FONT=Times New Roman]calibrate /dev/sdc1 00:00:00 ( SUCCESS ) [/FONT]
 
*[FONT=Times New Roman]path: /dev/sdc1[/FONT]*
*[FONT=Times New Roman]start: 34[/FONT]*
*[FONT=Times New Roman]end: 15624899324[/FONT]*
*[FONT=Times New Roman]size: 15624899291 (7.28 TiB)[/FONT]*
 
[FONT=Times New Roman]check file system on /dev/sdc1 for errors and (if possible) fix them 00:06:59 ( SUCCESS ) [/FONT]
 
***[FONT=Times New Roman]e2fsck -f -y -v /dev/sdc1[/FONT]***
 
*[FONT=Times New Roman]Pass 1: Checking inodes, blocks, and sizes[/FONT]*
*[FONT=Times New Roman]Pass 2: Checking directory structure[/FONT]*
*[FONT=Times New Roman]Pass 3: Checking directory connectivity[/FONT]*
*[FONT=Times New Roman]Pass 4: Checking reference counts[/FONT]*
*[FONT=Times New Roman]Pass 5: Checking group summary information[/FONT]*
 
*[FONT=Times New Roman]377821 inodes used (0.08%)[/FONT]*
*[FONT=Times New Roman]120 non-contiguous files (0.0%)[/FONT]*
*[FONT=Times New Roman]1335 non-contiguous directories (0.4%)[/FONT]*
*[FONT=Times New Roman]# of inodes with ind/dind/tind blocks: 0/0/0[/FONT]*
*[FONT=Times New Roman]Extent depth histogram: 368101/9706[/FONT]*
*[FONT=Times New Roman]1855061500 blocks used (94.98%)[/FONT]*
*[FONT=Times New Roman]0 bad blocks[/FONT]*
*[FONT=Times New Roman]194 large files[/FONT]*
 
*[FONT=Times New Roman]315923 regular files[/FONT]*
*[FONT=Times New Roman]61885 directories[/FONT]*
*[FONT=Times New Roman]0 character device files[/FONT]*
*[FONT=Times New Roman]0 block device files[/FONT]*
*[FONT=Times New Roman]0 fifos[/FONT]*
*[FONT=Times New Roman]1385821 links[/FONT]*
*[FONT=Times New Roman]4 symbolic links (4 fast symbolic links)[/FONT]*
*[FONT=Times New Roman]0 sockets[/FONT]*
*[FONT=Times New Roman]--------[/FONT]*
*[FONT=Times New Roman]1763633 files[/FONT]*
 
*[FONT=Times New Roman]e2fsck 1.41.9 (22-Aug-2009)[/FONT]*
 
[FONT=Times New Roman]grow partition from 7.28 TiB to 10.91 TiB 00:00:01 ( ERROR ) [/FONT]
 
*[FONT=Times New Roman]old start: 34[/FONT]*
*[FONT=Times New Roman]old end: 15624899324[/FONT]*
*[FONT=Times New Roman]old size: 15624899291 (7.28 TiB)[/FONT]*
 
[FONT=Times New Roman]check file system on /dev/sdc1 for errors and (if possible) fix them 00:06:23 ( SUCCESS ) [/FONT]
 
***[FONT=Times New Roman]e2fsck -f -y -v /dev/sdc1[/FONT]***
 
*[FONT=Times New Roman]Pass 1: Checking inodes, blocks, and sizes[/FONT]*
*[FONT=Times New Roman]Pass 2: Checking directory structure[/FONT]*
*[FONT=Times New Roman]Pass 3: Checking directory connectivity[/FONT]*
*[FONT=Times New Roman]Pass 4: Checking reference counts[/FONT]*
*[FONT=Times New Roman]Pass 5: Checking group summary information[/FONT]*
 
*[FONT=Times New Roman]377821 inodes used (0.08%)[/FONT]*
*[FONT=Times New Roman]120 non-contiguous files (0.0%)[/FONT]*
*[FONT=Times New Roman]1335 non-contiguous directories (0.4%)[/FONT]*
*[FONT=Times New Roman]# of inodes with ind/dind/tind blocks: 0/0/0[/FONT]*
*[FONT=Times New Roman]Extent depth histogram: 368101/9706[/FONT]*
*[FONT=Times New Roman]1855061500 blocks used (94.98%)[/FONT]*
*[FONT=Times New Roman]0 bad blocks[/FONT]*
*[FONT=Times New Roman]194 large files[/FONT]*
 
*[FONT=Times New Roman]315923 regular files[/FONT]*
*[FONT=Times New Roman]61885 directories[/FONT]*
*[FONT=Times New Roman]0 character device files[/FONT]*
*[FONT=Times New Roman]0 block device files[/FONT]*
*[FONT=Times New Roman]0 fifos[/FONT]*
*[FONT=Times New Roman]1385821 links[/FONT]*
*[FONT=Times New Roman]4 symbolic links (4 fast symbolic links)[/FONT]*
*[FONT=Times New Roman]0 sockets[/FONT]*
*[FONT=Times New Roman]--------[/FONT]*
*[FONT=Times New Roman]1763633 files[/FONT]*
 
*[FONT=Times New Roman]e2fsck 1.41.9 (22-Aug-2009)[/FONT]*
 
[FONT=Times New Roman]grow file system to fill the partition 00:00:01 ( SUCCESS ) [/FONT]
 
***[FONT=Times New Roman]resize2fs /dev/sdc1[/FONT]***
 
*[FONT=Times New Roman]resize2fs 1.41.9 (22-Aug-2009)[/FONT]*
*[FONT=Times New Roman]The filesystem is already 1953112411 blocks long. Nothing to do![/FONT]*
 
[FONT=Times New Roman]libparted messages ( INFO ) [/FONT]
 
*[FONT=Times New Roman]The backup GPT table is not at the end of the disk, as it should be. This might mean that another operating system believes the disk is smaller. Fix, by moving the backup to the end (and removing the old backup)?[/FONT]*
 
*[FONT=Times New Roman]Not all of the space available to /dev/sdc appears to be used, you can fix the GPT to use all of the space (an extra 7812456448 blocks) or continue with the current setting? [/FONT]*
 
*[FONT=Times New Roman]The backup GPT table is not at the end of the disk, as it should be. This might mean that another operating system believes the disk is smaller. Fix, by moving the backup to the end (and removing the old backup)?[/FONT]*
 
*[FONT=Times New Roman]Not all of the space available to /dev/sdc appears to be used, you can fix the GPT to use all of the space (an extra 7812456448 blocks) or continue with the current setting? [/FONT]*
 
*[FONT=Times New Roman]Unable to satisfy all constraints on the partition.[/FONT]*
[/FONT]
 
I'm not sure how to proceed with the libparted info and I can't find any useful information for me anywhere. I hoping the experts here can help me :D
 
Thanks for any help you can offer.

---

### Post by captainentropy on 2010-07-14
nobody? I'm getting desparate here. I need to get this server online with the added capacity. I have no idea how long it will take to complete registration on the gparted forum to ask that community (it's taking a looong time).
 
I've repeated this using a liveCD and the results were the same. 
 
I ran parted on it and it sees the disk as 12TB but after following the tutorial here [http://wiki.linuxmce.org/index.php/GPT](http://wiki.linuxmce.org/index.php/GPT) for resizing a partition table it still reports the end point as 8TB. ???

---

### Post by captainentropy on 2010-07-14
ok, even though parted reported 8TB I ran gparted on the drive and it grew the partition to 12TB. All is good now. All the data is there. I repeated this for the data array and it too is good.
 
Thanks me for helping me.

---

