---
title: "Partitioning question"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by satimis on 2010-09-26
Hi folks,

I installed a new HD on the PC which is a virtual machine to replace the old HD.  There are 2 HDs on the PC running Win7 and Ubuntu910 respectively with dual boot.

After disconnecting the old HD and adding the new HD, I booted up the machine with Ubuntu 10.04-1 installer paritioning the new HD and installing the OS.  Installation went through without complaint and finally Ubuntu 10.04 started.

The partition on the new HD is as follow;```

/root
/home
/kvm

```

(kvm is for keeping the guests of KVM, the virtualizer)

Then I reconnected the old HD and booted up Ubuntu910

$ sudo fdisk -l```

[sudo] password for satimisu910: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c92e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      118707   953510912   83  Linux
/dev/sda2          118707      121602    23248897    5  Extended
/dev/sda5          118707      121602    23248896   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a4bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      118706   953505913+  83  Linux
/dev/sdb2          118707      121601    23254087+   5  Extended
/dev/sdb5          118707      121601    23254056   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d09a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9729    78148161    7  HPFS/NTFS

```


$ sudo mount -t ext4 /dev/sda1 /mnt
$ ls /mnt/```

bin   etc         lib    lost+found  opt   sbin     sys  var
boot  home        lib32  media       proc  selinux  tmp  vmlinuz
dev   initrd.img  lib64  mnt         root  srv      usr

```

$ ls /mnt/home/```

satimisub1004

```
which is /home of user.  However it is on /root NOT on /home partition.

Furthermore I can't find /kvm partition.

Please advise where I went wrong?  TIA

B.R.
satimis

---

