---
title: "ERRNO 5 Input/Output Error on Samsung SSD PM851"
date: 2015-11-03
forum: Installation &amp; Upgrades
---

### Post by seb8 on 2015-11-03
Trying to install 15.10 on a Dell Latitude E5450 and am having problem with the installer returning ERRNO 5 Input/Output Error which looks to be related to the SSD a Samsung SSD PM851 [ext08d0q]

Here are some logs from running ubiquity in debug mode. Same error on 14.04 too with automatic partitioning and manual. Have run a read/write test from the live cd on the /dev/sda device and it looks happy. Any help appreciated.

=== kern.log
Nov  3 11:39:28 ubuntu kernel: [   86.271277] EXT4-fs (sda2): unable to read superblock
Nov  3 11:39:28 ubuntu kernel: [   86.272131] EXT4-fs (sda2): unable to read superblock
Nov  3 11:39:28 ubuntu kernel: [   86.272947] EXT4-fs (sda2): unable to read superblock
Nov  3 11:39:28 ubuntu kernel: [   86.273931] FAT-fs (sda2): bogus number of reserved sectors
Nov  3 11:39:28 ubuntu kernel: [   86.273934] FAT-fs (sda2): Can't find a valid FAT filesystem
Nov  3 11:39:28 ubuntu kernel: [   86.282938] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sda2
Nov  3 11:39:28 ubuntu kernel: [   86.285928] XFS (sda2): Invalid superblock magic number
Nov  3 11:39:28 ubuntu kernel: [   86.287263] FAT-fs (sda2): bogus number of reserved sectors
Nov  3 11:39:28 ubuntu kernel: [   86.287266] FAT-fs (sda2): Can't find a valid FAT filesystem
Nov  3 11:39:28 ubuntu kernel: [   86.290180] MINIX-fs: unable to read superblock
Nov  3 11:39:28 ubuntu kernel: [   86.296336] attempt to access beyond end of device
Nov  3 11:39:28 ubuntu kernel: [   86.296339] sda2: rw=16, want=3, limit=2
Nov  3 11:39:28 ubuntu kernel: [   86.296341] hfsplus: unable to find HFS+ superblock
Nov  3 11:39:28 ubuntu kernel: [   86.297655] qnx4: no qnx4 filesystem (no root dir).
Nov  3 11:39:28 ubuntu kernel: [   86.298677] ufs: You didn't specify the type of your ufs filesystem
Nov  3 11:39:28 ubuntu kernel: [   86.298677] 
Nov  3 11:39:28 ubuntu kernel: [   86.298677] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
Nov  3 11:39:28 ubuntu kernel: [   86.298677] 
Nov  3 11:39:28 ubuntu kernel: [   86.298677] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Nov  3 11:39:28 ubuntu kernel: [   86.299563] hfs: can't find a HFS filesystem on dev sda2

Attached full log bundle.

---

### Post by ubfan1 on 2015-11-03
sda2 is your extended partition, which just contains all the logicals (sda5, sda6,...).  Do not refer to it directly for anything.

---

