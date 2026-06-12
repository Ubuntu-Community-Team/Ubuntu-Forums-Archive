---
title: "dual boot problem"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by go_beep_yourself on 2008-01-11
Here's what I have, and what I'd like to do.

```
[root@localhost ~]# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23498   188747653+   7  HPFS/NTFS
/dev/sda2           23499       23511      104422+  fd  Linux raid autodetect
/dev/sda3           23512       36565   104856255   fd  Linux raid autodetect
/dev/sda4           36566       38913    18860310    5  Extended
/dev/sda5           36566       36630      522081   82  Linux swap / Solaris
/dev/sda6           36631       38913    18338166   fd  Linux raid autodetect

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3b6e3b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23498   188747653+   7  HPFS/NTFS
/dev/sdb2           23499       23511      104422+  fd  Linux raid autodetect
/dev/sdb3           23512       36565   104856255   fd  Linux raid autodetect
/dev/sdb4           36566       38913    18860310    5  Extended
/dev/sdb5           36566       36630      522081   82  Linux swap / Solaris
/dev/sdb6           36631       38913    18338166   fd  Linux raid autodetect

Disk /dev/md2: 37.5 GB, 37556322304 bytes
2 heads, 4 sectors/track, 9169024 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 107.3 GB, 107372675072 bytes
2 heads, 4 sectors/track, 26214032 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 106 MB, 106823680 bytes
2 heads, 4 sectors/track, 26080 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
[root@localhost ~]# 
```

Windows xp 64 bit continuously crashes. I've tried people's suggestions and did chkdsk /r and defrag. That didn't help at all. I even disabled something about restart on error.  I'd rather not have Windows, but I need it for many games because I have an 8800 gts. Last time I began to install xp after I had Linux, I got to the part of the installation for partitioning. Windows didn't show any of my ext3 partitions. I then rebooted without doing anything, and my ext3 partitions were gone. I then booted from a live cd and used testdisk to recover them. I hear of many people installing xp after Linux. They just had to reinstall Grub. How can I do it?

---

### Post by Partyboi2 on 2008-01-11
This explains how
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

