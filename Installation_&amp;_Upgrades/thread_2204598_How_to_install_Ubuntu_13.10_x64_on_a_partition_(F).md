---
title: "How to install Ubuntu 13.10 x64 on a partition (F:) alongside with windows 7"
date: 2014-02-09
forum: Installation &amp; Upgrades
---

### Post by Mr-Bledi on 2014-02-09
Hello all. i'm trying or figure it out how to install ubuntu the lattest one in F: 
i have windows as my primary os, and want to use dual boot, and so created an partition for F: about 60GB to install it and use dual boot.
tried first,  to do it, following a partition scheme and ended up with no dual boot no boot neither! 
help please?

---

### Post by fantab on 2014-02-09
Boot with Ubuntu DVD/USB and 'Try ubuntu without installing'. Open Terminal [Ctrl+Alt+T] run and post the output of the following commands:
```
sudo parted -l
sudo fdisk -l
```

Can you boot Windows?

---

### Post by mastablasta on 2014-02-10
> **Mr-Bledi said:**
> Hello all. i'm trying or figure it out how to install ubuntu the lattest one in F: 
i have windows as my primary os, and want to use dual boot, and so created an partition for F: about 60GB to install it and use dual boot.
tried first, to do it, following a partition scheme and ended up with no dual boot no boot neither! 
help please?

there is no F: in linux. you would have to delete F and then use the unallocated disk space to install ubuntu to it (install to largest free disk space option).

post copy the above comands in terminal and post the output here. windows is still there unless you chose to format the whole disk during install.

---

### Post by Mr-Bledi on 2014-02-10
> **fantab said:**
> Boot with Ubuntu DVD/USB and 'Try ubuntu without installing'. Open Terminal [Ctrl+Alt+T] run and post the output of the following commands:
```
sudo parted -l
sudo fdisk -l
```

Can you boot Windows?
[B][I]yeah with no problem. allright i'm doing it and will post the results
[/I][/B]
> **mastablasta said:**
> there is no F: in linux. you would have to delete F and then use the unallocated disk space to install ubuntu to it (install to largest free disk space option).

post copy the above comands in terminal and post the output here. windows is still there unless you chose to format the whole disk during install.

***yeah, i figure that out too, so now it is unllocated... i will post the results here thanks!! :)***

---

### Post by Mr-Bledi on 2014-02-10
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HN-M500M (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   436GB  436GB  primary  ntfs


Model: SanDisk Cruzer Edge (scsi)
Disk /dev/sdb: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8004MB  8003MB  primary  fat32        boot, lba
```


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xb823ba95

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   850939903   425366528    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8004 MB, 8004304896 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00e29a01

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15633407     7815680    c  W95 FAT32 (LBA)

```


there are my results
a screenshot of parts [http://i.minus.com/jbz9RuqlvZ36yW.png](http://i.minus.com/jbz9RuqlvZ36yW.png)

---

### Post by mastablasta on 2014-02-10
boot repair tool on live CD should be able to restore the boot. 

if not, windows is still there, so using windows boot repair command from windows console will work as well. instructions: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

do not use wubi on disk to install the OS. boot from the CD and install into empty disk space. my siganture has link to ubuntu manual. should be a good place to start. if oyu have any quesitons don't hesitate to ask them here. though it is good if you do a bit of search on your own as well ;-)

try it before installing it: [http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

how to install 1 (detailed):[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
how to install 2 (easy with pics): [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

how to safely install inside windows using virtualbox (how-to with pics): [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox) <<-- this is really good for trying out the OS and testing various stuff without worrying you will break anything. just make a snapshot before you mess arround with OS and you can quickly restore it to defaults after the mess.

---

