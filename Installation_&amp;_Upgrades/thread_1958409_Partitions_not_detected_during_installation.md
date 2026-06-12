---
title: "Partitions not detected during installation"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by BLaZuRE on 2012-04-14
I already [re]installed Windows 7  as the first primary partition and have an extended partition with logical partitions.  Inbetween, I have about 60 some GBs unallocated, which I was planning to use for Kubuntu 11.10 amd64 and another distro (or 2).

However, when I am asked to manually setup the partitions, it sees the hard drive with no partition table.  The only option I have is create a new table and partition away.

I've also tried running Kubuntu from CD and checking the partition manager from there, but no luck.  Windows 7 can be booted normally.

---

### Post by darkod on 2012-04-14
No partitions displayed can mean error in the partition table. Windows often ignores there errors and seems to work normally, but ubuntu doesn't ignore them and doesn't show partitions.

It's best to boot into live mode first, and check the partitions with:
sudo fdisk -l (small L)

Post the output and we'll see if it finds something.

Another option is if you have raid meta data remains, if the disk was used in raid before. In that case ubuntu will ignore it not being sure how you want to use it. But in this case it doesn't show a disk existing at all usually.

---

### Post by BLaZuRE on 2012-04-14
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0cb80cb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   126035967    62914560    7  HPFS/NTFS/exFAT
/dev/sda3       213086208   625153409   206033601    f  W95 Ext'd (LBA)
/dev/sda5       213086223   215046070      979924   82  Linux swap / Solaris
/dev/sda6       215046153   583178232   184066040    7  HPFS/NTFS/exFAT
/dev/sda7       583178240   625119231    20970496    6  FAT16
ubuntu@ubuntu:~$ 


sda1 looks like the 100 MB system partition Windows 7 said it had to put on there
sda2 looks like the Windows 7 partition

sda3 looks like the extended partition containing
   sda5 Linux swap?  (don't remember if that's where it was located)
   sda6 Files partition (NTFS)
   sda7 Small FAT16 because I was testing around with it
   a small amount of Free Space (not unallocated space to Windows).

---

### Post by BLaZuRE on 2012-04-14
[IMG]http://i41.tinypic.com/fviagp.png[/IMG]This is how it looks in Windows if it helps any.

---

### Post by darkod on 2012-04-14
Windows Disk Management shows a 957MB primary partition with no filesystem defined, while fdisk has only two primary partitions and the extended one.

I don't know exactly what but something is wrong and they show different data.

If you have no data on the 957MB partition (it seems to have no filesystem), delete it from windows Disk Management.

See if that will make kubuntu show the partitions during install.

---

### Post by BLaZuRE on 2012-04-14
No, deleting that partition (which was not created by windows, I suspect that was the swap) did not help.  When I deleted, Windows Disk Manager included it back in the extended partition as "Free Space".

K/Ubuntu still show no partition table for the drive when attempting to install.

---

### Post by oldfred on 2012-04-14
Normally we run the bootinfoscript to resolve issues with Linux, but it does try to mount partitions and may show the same error that gparted is having trouble with.

You can run it from this as a download into the Ubuntu liveCD, or as a liveCD on its own. Or you can just download script and run it. Darko has a link in his signature directly to boot script.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

It may not show much, but I am hoping it will show some error in partition table, NTFS partitions, or other issue.

---

### Post by BLaZuRE on 2012-04-14
[http://paste.ubuntu.com/930341/](http://paste.ubuntu.com/930341/) (after boot-repair)

Hmmm ... now for some detective work :(

edit:
No, Linux still won't see partitions.  Also, I got [URL="http://paste.ubuntu.com/930354"]http://paste.ubuntu.com/930354
[/URL] 
which has less errors on it.

---

### Post by oldfred on 2012-04-14
Your extended partition end beyond the end of the disk.
> 
/dev/sda3 ends after the last sector of /dev/sda

First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sda > parts_sda.txt

Then download and run this program.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by darkod on 2012-04-15
Yeah, I missed that from the fdisk output. How come running fdisk -l doesn't give the message also?

---

### Post by Quackers on 2012-04-15
fdisk -l doesn't give a message but it gives the info 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, [COLOR="Red"]total 625142448 sectors[/COLOR]
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0cb80cb7

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 206847 102400 7 HPFS/NTFS/exFAT
/dev/sda2 206848 126035967 62914560 7 HPFS/NTFS/exFAT
/dev/sda3 213086208 [COLOR="Red"][COLOR="Red"]625153409[/COLOR][/COLOR] 206033601 f W95 Ext'd (LBA)
/dev/sda5 213086223 215046070 979924 82 Linux swap / Solaris
/dev/sda6 215046153 583178232 184066040 7 HPFS/NTFS/exFAT
/dev/sda7 583178240 625119231 20970496 6 FAT16

---

### Post by oldfred on 2012-04-15
I missed it also, and I was just suspecting boot script might show something else as the problem. But boot script processes some of the data and makes it easier to see some of the issues.

---

### Post by BLaZuRE on 2012-04-15
> **oldfred said:**
> I missed it also, and I was just suspecting boot script might show something else as the problem. But boot script processes some of the data and makes it easier to see some of the issues.

Ya, we all missed it.

I used TestDisk a while back and that's probably what caused the oversized extended partition.  All I needed to do was (after installing):
[INDENT][I] sudo fixparts /sda
w [hit **enter** key to quit program]
[/I][/INDENT]and it automatically fixed it!

Thank you for your help!

---

