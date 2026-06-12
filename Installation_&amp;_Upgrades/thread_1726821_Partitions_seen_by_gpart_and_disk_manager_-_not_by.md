---
title: "Partitions seen by gpart and disk manager - not by installer"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by TexasKen on 2011-04-11
Wanting to dual boot XP with UBUNTU.
Live CD verified good.



ran df in terminal:

ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   1030436     66624    963812   7% /
none                   1024524       248   1024276   1% /dev
/dev/sr0                709792    709792         0 100% /cdrom
/dev/loop0              676480    676480         0 100% /rofs
none                   1030436       332   1030104   1% /dev/shm
tmpfs                  1030436        24   1030412   1% /tmp
none                   1030436        96   1030340   1% /var/run
none                   1030436         4   1030432   1% /var/lock

Ran sudo fdisk -lu in terminal:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   204796619   102398278+   7  HPFS/NTFS
/dev/sda2       204797952   266235903    30718976   83  Linux
/dev/sda3       308801430   390716864    40957717+   7  HPFS/NTFS
/dev/sda4       266235904   308799487    21281792   83  Linux

Partition table entries are not in disk order


Originally I had two partitions for Windows xp of 100 gig each. I cleared / backed up the second partition and created two 50 gig partitions, splitting the second into two linux (using Gparted) partitions labelled root and swap.

Disk Utility sees this hdd as a RAID component. It is connected through a RAID controller.

The installer (in allocate drive space step) doesn't see them for some reason. 

Hardware:
AMD Athlon 64+clawhammer processor
Asus A8N-SLI mobo
hdd as above
2 Gig RAM
DVD / CD Burner

Any help is appreciated

---

### Post by Mark Phelps on 2011-04-11
I believe that you have to use the Alternate installer with a system that is using RAID.  The standard desktop version can't install in a RAID system.

---

### Post by TexasKen on 2011-04-11
Thank you, I will download that iso and try that.

Ken

---

### Post by Quackers on 2011-04-11
If you are using raid I believe you can install kpartx to the live cd desktop and the installer may then see the raid array. It worked for me, however, grub installation did not go well for me, but many other users have managed it.

---

### Post by TexasKen on 2011-04-11
I am a dummy. I since created extended partitions with one designated as / (root) now I cannot get windows to boot. any suggestions? the files etc are still there on that partition, but my hardware does not see it as a bootable partition.

---

### Post by TexasKen on 2011-04-11
Two words:

Boot Flag

'nuf said.

---

### Post by mosborne41 on 2012-12-21
I had a similar problem although gpart didn't see the partition either.   After much forum review and many trials and errors I realized that my partition table was messed up.  It looked like I had primary partions in extended partions is my guess.  I found a program by Rod Smith called FixParts that cleaned up my partion table and everything worked fine.

---

### Post by coffeecat on 2012-12-21
Old thread closed.

---

