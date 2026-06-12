---
title: "Ubuntu 10.10 and Win7"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by maxcraft on 2010-11-30
I did upgrade my Ubuntu on 10.10 and had always a Dual-Boot with Win7

After the install of Ubuntu, my grub wouldn't work anymore. I could only boot into Ubuntu, but GRUB didn't even appear. I already tried 
> sudo update-grubbut this brought only the installs for Ubuntu and GRUB didn't start.
Afterwards I tried to recover my MBR with the help of my Win7 DVD, but this didn't work out too. Now I can't boot neither Ubuntu nor Win7 and have to run from the Live-CD.

I also tried to fix it with
> sudo grub
root (hd0,0)
setup (hd0)but setup(hd0) only returned, Error 17: Cannot mount etc.

What can I do? I need my Windows for work and I don't want to reinstall neither Ubuntu nor Win7.

Output of fdisk -l gives:
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x131d70a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2               1         192     1536000   27  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3             192         205      102400   42  SFS
Partition 3 does not end on cylinder boundary.
/dev/sda4             205       19457   154648576   42  SFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00047141

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18693   150145024   83  Linux
/dev/sdb2           18693       19458     6142977    5  Extended
/dev/sdb5           18693       19458     6142976   82  Linux swap / Solaris

---

### Post by zazlox on 2010-11-30
check this :

[http://ubuntuforums.org/showthread.php?t=732307](http://ubuntuforums.org/showthread.php?t=732307)

---

### Post by maxcraft on 2010-11-30
Gonna try it. Thx!

---

### Post by oldfred on 2010-11-30
Your windows partitions have changed from basic to sfs. SFS is a windows only partitioning scheme that is compatible with nothing. Windows automatically converts to it if you try to create more than 4 partitions and it is like LVM, a logical volume manager.

Windows says you cannot convert back withour copying all  your data and reformating completely.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec)

---

