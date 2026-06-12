---
title: "Dual-boot corrupted and Windoze lost due to BT4 install and partition resize"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by kelphiri on 2010-08-04
My machine had Vista in one partition and the other partition i installed Ubuntu 10.0.4 a few days ago. A little later i got BackTrack 4 which i also wanted and upon install the installer asked to resize the partitions and went on to install BT4. When i rebooted i got stuck in GRUB prompt and could not boot any other OS except LiveCD.

Here are the results from the terminal:
ubuntu@ubuntu:~$ cat /etc/issue
Ubuntu 10.04 LTS \n \l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe90be90b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10240    82251776    6  FAT16
/dev/sda2           10241       12819    20715817+   f  W95 Ext'd (LBA)
/dev/sda3           12820       12820        4264+   7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4   *       12820       19457    53315470+  83  Linux
/dev/sda5           10241       12706    19808113+  83  Linux
/dev/sda6           12707       12819      907641   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

Gparted lists the drives as unformatted and unknown

I tried fixing the MBR with Spotmau but still wont boot, it says "error loading OS"

---

