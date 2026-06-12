---
title: "Ubuntu 11.04 and Windows7 parallel doesn't work"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by nearlymagicman on 2011-10-31
I just installed Windows7 and afterwards Ubuntu11.04 so I wont have trouble with grub, but grub doesn't even load after installation finished. 
I now tried to restore grub using [http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html]("http://[URL=%22http://[URL%22") but already typeing in "sudo fdisk -l" resorts in a very different output, as only sdb1 is there even though there should be at least 6 sdb considering Gparted output.

I am quite lost here as this parallel installation always worked for me this way. I am using a ThinkPad x121e, could this have something to do with it?[ ]("http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html")

This is the output of fdisk

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x87c20926

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38914   312571223+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 1029 MB, 1029963776 bytes
32 heads, 62 sectors/track, 1013 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009d301

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1013     1004865    c  W95 FAT32 (LBA)

```
[ ]("http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html")

---

