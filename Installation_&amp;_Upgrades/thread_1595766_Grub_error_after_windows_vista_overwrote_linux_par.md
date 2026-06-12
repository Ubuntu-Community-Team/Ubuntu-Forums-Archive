---
title: "Grub error after windows vista overwrote linux partitions"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by shponglelized on 2010-10-13
okay ive got this situation which i can' t get out of.

Ive been  dualbooting ubuntu 10.04 with windows 7 (an upgrade from windows vista),  which was running very well, besides 1 tricky thing in grub. I could  not remove the windows vista entry in grub, a friend of mine accidently  selected it and grub  *gave error: No* such partition. First I  thought i had lost my data but when running test disk i found out that  just my partitions were removed. Troughout testdisk i got them back,   after restoring when i give sudo fdisk -l   when running 10.04 live cd  the output is: 

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255  heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 *  512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512  bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk  identifier: 0x6aa46911

   Device Boot      Start         End       Blocks   Id  System
/dev/sda1   *           1        2350     18874368    7  HPFS/NTFS                 (PQService windows partition)
/dev/sda2             2350       11469    73242180+   7  HPFS/NTFS             (windows 7  partition)
/dev/sda3           11469       16332    39062528   83   Linux                       (/ partition)
/dev/sda4            16332       77826   493956792    f  W95 Ext'd (LBA)       (no idea? live  cd partition?)
/dev/sda5           16332       39053   182510592    83  Linux                        (/home partition)        
/dev/sda6            39054       40087     8305564   82  Linux swap / Solaris   (/swap  partition)
/dev/sda7           40088       77500   300510548+   7   HPFS/NTFS              (data partion used dualstoragedisk between the  two OS's) 
/dev/sda8           77565       77826     2095448    c   W95 FAT32 (LBA) (Dos partition?)

So the PQservice and Dos  partition were hidden before, and after testdisk they don't seem to be  anymore....
Big question is:
All my data and OS's seem to be  intact, but how do i restore grub that i can get my bootmenu with linux,  win7 back, cuz now neither of them is able to boot.)
Thanks a lot.

---

