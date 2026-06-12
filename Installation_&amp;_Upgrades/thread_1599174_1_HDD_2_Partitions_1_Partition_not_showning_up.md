---
title: "1 HDD 2 Partitions 1 Partition not showning up"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by F12OST on 2010-10-17
i just installed ubuntu 10.10 im using it now but my 2nd partition that got all my backed up files on is not showin up so i ask how do i get to use it ? and another thing is when i was installing the backup partition said it has no MB used ????

---

### Post by F12OST on 2010-10-17
any1 please

---

### Post by JackNocturne on 2010-10-17
post the output of  ```
sudo fdisk -l
``` in terminal

---

### Post by F12OST on 2010-10-17
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11ac3300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+  83  Linux
/dev/sda2           12749       38912   210162299+   f  W95 Ext'd (LBA)
/dev/sda5           12749       38912   210162298+  82  Linux swap / Solaris

---

### Post by JackNocturne on 2010-10-17
my suggestion is use **Gparted** (System>Administration>xxx) to **check file.system** (/dev/sda2  i assume this your backup partition) for errors  

#**important **>Don't perform file system check of partition that is mounted(so in short make sure that the partition your planning to check for errors is unmounted)

---

### Post by F12OST on 2010-10-17
i think it /dev/sda5 plus im new to ubuntu well linux

---

### Post by F12OST on 2010-10-17
dont know what im doin with that gparted

---

### Post by florus on 2010-10-17
Looks like your second partition is fully occupied by your swap partition. No room left for your backup files.
sda5 is a logical partition within your extended partition sda2

---

### Post by F12OST on 2010-10-17
no i think sda5 had my files on from my previous os win 7  how do i acess my files what are on there

---

### Post by florus on 2010-10-17
There is a good article on disk partitioning at [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by florus on 2010-10-17
> no i think sda5 had my files on from my previous os win 7  how do i acess my files what are on there
If your windows partition still exists, it will be listed under 'Places' in the bar at the top of your screen.

---

### Post by JackNocturne on 2010-10-17
it seems ubuntu is using your backup partition as swap (i dont know why) 

disable swap for a moment and try accessing your files

```
sudo swapoff -a
``` in terminal

See if you can access now

---

### Post by F12OST on 2010-10-17
tried the sudo swapoff -a and this is what i get 
sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11ac3300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+  83  Linux
/dev/sda2           12749       38912   210162299+   f  W95 Ext'd (LBA)
/dev/sda5           12749       38912   210162298+  82  Linux swap / Solaris

still not sure how to view the files im a noobie 

to [florus]("http://ubuntuforums.org/member.php?u=454057")  ubuntu has overwriten the win 7 partition and sda2 or sda5 partition contains well should contain my backup files

---

### Post by JackNocturne on 2010-10-17
after u have swapped off with the command i gave you, make sure its swapped off by checking the the output of the following command ```
sudo swapon -s
```If it returns blank then good for now:)


If above successful mount your partition by
```
sudo mount -t vfat /dev/sda2 /mnt
```Check the contents of /mnt after that, **should** be there

---

### Post by florus on 2010-10-17
Your disk has two main partitions.
sda1 is a primary partition
sda2 is an extended partition
sda5 is a logical partition which exists inside sda2
You cannot have date directly in sda2, only in the logical partition inside it.
I hope I am wrong, but I think Gparted has formatted sda5 as a linux swap partition erasing the data in it. Whether it is possible to recover the data is far outside my knowledge.

---

### Post by F12OST on 2010-10-17
~$ sudo swapon -s
Filename                Type        Size    Used    Priority

:~$ sudo mount -t vfat /dev/sda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


that what comes up and i hope florus my data not been erased :(

btw i really appreciate the help

---

### Post by florus on 2010-10-17
>  i hope florus my data not been erased
I hope that too. Just don't suspend or hibernate your computer, as that would write data into the swap partition.
BTW, I think you should have run JackNocturne's suggestion on sda5, not sda2. Does Jack agree with that?

---

### Post by JackNocturne on 2010-10-17
I hope its not the :(case your backup got overwritten 

try again mounting by just ```
sudo mount /dev/sda5 /mnt
```


I agree with florus, try the option with sda5

---

### Post by oldfred on 2010-10-17
If you have written anything into where the partition was you may not be able to recover it.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

May recover files but they will not have original names:
Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Foremost
[http://www.howtoforge.com/recover-deleted-files-with-foremost](http://www.howtoforge.com/recover-deleted-files-with-foremost)
[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)
sleuthkit is in repositories:
[http://www.sleuthkit.org/sleuthkit/](http://www.sleuthkit.org/sleuthkit/).

---

### Post by JackNocturne on 2010-10-17
If all fails do as **above post**

---

### Post by F12OST on 2010-10-17
:~$ sudo mount /dev/sda5 /mnt
/dev/sda5 looks like swapspace - not mounted
mount: you must specify the filesystem type

---

### Post by florus on 2010-10-17
If you have not hibernated your computer, you will probably not have overwritten anything. I THINK that you need to use Gparted to reformat sda5 as NTFS, but I would like confirmation from someone more expert than I. Good luck.

---

### Post by F12OST on 2010-10-17
if i reformat i will lost the data i dont wont to use a program where it will recover files but with names useless to me :(

---

### Post by florus on 2010-10-17
sda5 will have to be reformatted back to its original filesystem before it can be read. The trouble is, I am not sure how to do it non-destructively. Perhaps oldfred can advise.

---

### Post by F12OST on 2010-10-17
that a bit bend

---

### Post by florus on 2010-10-17
> that a bit bend???
I mean that you have effectively unformatted sda5 as a swap partition has no filesystem. Somehow we have to tell sda5 that it is an NTFS partition (assuming it was not formatted as FAT), and the only way I know is using Gparted. Your data may well still be intact, so keep hoping, and wait for some more expert guidance.

---

### Post by F12OST on 2010-10-17
yeah, fingers crossed

---

### Post by F12OST on 2010-10-17
anybody with some info please

---

### Post by JackNocturne on 2010-10-18
Hey did you try running **testdisk** to see if your partition was written over? You can download it quickly in terminal ```
sudo apt-get install testdisk
```After it's installed run ```
sudo testdisk
```
You can analyse your disk,it will give more information
[http://i1021.photobucket.com/albums/af334/JackNocturne/Screenshot-1-1.png](http://i1021.photobucket.com/albums/af334/JackNocturne/Screenshot-1-1.png)

---

### Post by F12OST on 2010-10-18
> **JackNocturne said:**
> Hey did you try running **testdisk** to see if your partition was written over? You can download it quickly in terminal ```
sudo apt-get install testdisk
```After it's installed run ```
sudo testdisk
```You can analyse your disk,it will give more information
[http://i1021.photobucket.com/albums/af334/JackNocturne/Screenshot-1-1.png](http://i1021.photobucket.com/albums/af334/JackNocturne/Screenshot-1-1.png)


im running that right now

---

### Post by F12OST on 2010-10-19
i ran that testdisk and this is the outcome of the analyse thing it  took all night 

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63

The harddisk (320 GB / 298 GiB) seems too small! (< 1922 GB / 1790 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  Mac HFS                534594840 3755828569 3221233730 [CÔM- ^_M-5&~L}M-8M-:-M
  MS Data                625121279 1045445875  420324597
  MS Data                625139711 1250072574  624932864








[ Continue ]
NTFS, 319 GB / 297 GiB


what should i do next what one do i click on for my backup drive the bigger partition thanks

---

