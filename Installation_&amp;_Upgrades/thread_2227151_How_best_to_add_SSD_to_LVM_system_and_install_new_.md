---
title: "How best to add SSD to LVM system and install new version?"
date: 2014-05-31
forum: Installation &amp; Upgrades
---

### Post by lindsayward on 2014-05-31
Hi, and thanks in advance for replying!
I have an existing 12.04 system with 2 HDDs setup using LVM, and I want to know the best way to add my new SSD and install 14.04 on it (best in terms of performance and maintainability).

I think I would like to keep using LVM, but I'm not sure how best to combine/move or start over for the LVs, and what should be on the SSD and what should stay on the HDDs. I am thinking I could do a fresh install to the SSD and leave the existing install as is, until I get it right (safety), then somehow reclaim the space on the current HDDs... maybe.

I use the system for MythTV (run ubuntu rather than mythbuntu though), hence the large "movies" drive. 
Here are some details of the current system...
I have connected the new SSD (called sdc) but not done anything to it yet.

```

**fdisk -l**
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbc04db52

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  3907029167  1953513560   83  Linux

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d1e6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      976895      487424   83  Linux
/dev/sdb2          976896  3907028991  1953026048   8e  Linux LVM

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/vg-lvroot: 20.0 GB, 19998441472 bytes
255 heads, 63 sectors/track, 2431 cylinders, total 39059456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/vg-lvhome: 9999 MB, 9999220736 bytes
255 heads, 63 sectors/track, 1215 cylinders, total 19529728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/vg-lvswap: 4999 MB, 4999610368 bytes
255 heads, 63 sectors/track, 607 cylinders, total 9764864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/vg-lvmovies: 3965.3 GB, 3965290807296 bytes
255 heads, 63 sectors/track, 482085 cylinders, total 7744708608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

**pvdisplay**
  --- Physical volume ---
  PV Name               /dev/sdb2
  VG Name               vg
  PV Size               1.82 TiB / not usable 4.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476812
  Free PE               0
  Allocated PE          476812
  PV UUID               XHeIXt-d3xr-Wo1f-rZF9-7rCm-nvey-AfJ0QU
   
  --- Physical volume ---
  PV Name               /dev/sda1
  VG Name               vg
  PV Size               1.82 TiB / not usable 4.09 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476931
  Free PE               0
  Allocated PE          476931
  PV UUID               AYUyq4-1YYp-kOK2-FYyB-qRjV-nZKx-vie8lT

**vgdisplay**
  --- Volume group ---
  VG Name               vg
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  26
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                4
  Open LV               4
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               3.64 TiB
  PE Size               4.00 MiB
  Total PE              953743
  Alloc PE / Size       953743 / 3.64 TiB
  Free  PE / Size       0 / 0   
  VG UUID               KoLIJC-xIB9-uKKh-Q7Ba-nfQR-Hf8I-OqsXS5
   
**lvdisplay**   
  --- Logical volume ---
  LV Name                /dev/vg/lvroot
  VG Name                vg
  LV UUID                iNv6Ss-DDbi-IFdG-dSmB-Ewee-Rxzc-AZvI8L
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                18.62 GiB
  Current LE             4768
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/vg/lvhome
  VG Name                vg
  LV UUID                rEKL7X-nsFk-qpu1-jAVG-ENzm-w1la-igpQRb
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                9.31 GiB
  Current LE             2384
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/vg/lvswap
  VG Name                vg
  LV UUID                VfIbym-pFvq-Izkc-G0aa-9Yb4-3EXo-UwwPr4
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                4.66 GiB
  Current LE             1192
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
  --- Logical volume ---
  LV Name                /dev/vg/lvmovies
  VG Name                vg
  LV UUID                6Xdubx-0I0S-2dWu-cvNz-2jlU-EUWy-dA7qbr
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                3.61 TiB
  Current LE             945399
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3
   
**df -h**
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/vg-lvroot     19G  6.1G   12G  35% /
udev                     1.7G  4.0K  1.7G   1% /dev
tmpfs                    690M 1016K  689M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     1.7G  108K  1.7G   1% /run/shm
/dev/sdb1                473M   53M  398M  12% /boot
/dev/mapper/vg-lvhome    9.3G  3.1G  5.8G  35% /home
/dev/mapper/vg-lvmovies  3.6T  1.8T  1.7T  51% /movies

```

Let me know if there is any other info that would be useful, and thank you for taking the time to help me out!

---

### Post by oldfred on 2014-05-31
I am not a fan of LVM, but in your case where you want one large movie partition, I guess it makes sense.
The main disadvantage I see is that if any drive fails you lose all data on both drives.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

 sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

I would just use SSD as / & /home. Then entire LVM drives could be your movies and system would be very fast.
Another recent thread on SSD (only).
[http://ubuntuforums.org/showthread.php?t=2227050](http://ubuntuforums.org/showthread.php?t=2227050)

If Linux only I do prefer to use gpt partitioning, just because it also has a backup for reliability.
      GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by lindsayward on 2014-05-31
Thanks heaps for the reply.
I liked the idea of LVM, but I don't think it really helps much in my situation, and I had a nightmare experience trying to add a new disk ([LVM problem after adding new disk]("http://ubuntuforums.org/showthread.php?t=2225874")). So, I would be happy to start fresh WITHOUT LVM if that's simple enough to do.
MythTV allows me to specify multiple "storage groups" so I can spread my movies over new disks any time without much effort. This lets MythTV spread the load over multiple disks, but I'm actually unsure how LVM affects this, since MythTV sees it as one volume, I think. It might even be better with different volumes. Does anyone know?

Also, my SSD is 120GB and I don't need nearly that much space for / and /home (see df output above), but anyway...

So, what would be the best and safest way to reinstall without LVM and still be able to access the files that are in LVs at the moment?

---

### Post by oldfred on 2014-05-31
I can move thread to MythUbuntu or multimedia sub-forum where those with Myth may see thread.

You can just install Ubuntu to SSD and then add the software to mount & use existing LVM. No idea about Myth issues. When I install I see it uninstalling software I do not use & that includes RAID & LVM. I hate that it uninstalls gparted as that is one of the first things I reinstall. I have several drives so I can use gparted on all but my system drive.

---

### Post by lindsayward on 2014-05-31
Thanks. My main issues are not about MythTV, and I do not use Mythbuntu. I tried it first, but realised I had to keep installing standard software I wanted, so now I use normal/full ubuntu.
So: install ubuntu 14.04 to the SSD (perhaps using 20GB for / and 100GB for /home?)
Then install LVM2 and mount the existing LVs...
Then, how could I "get out of" LVM??

---

### Post by oldfred on 2014-05-31
I think the only way is to fully backup and then remove the LVM and repartition.

The format is so different there is no way to convert. It is logical partitions overlayed over the physical partitions.

---

### Post by lindsayward on 2014-06-01
Thanks. I think I'll install with / and /home on the SSD (not using LVM), then mount the existing LVM partitions...
Then copy the old LVM /home from the HDD into the new one, install programs and get my settings right, then try and reclaim the space used by the LVM partitions I won't keep using... and keep only the /movies.
Let's see how we go...

---

