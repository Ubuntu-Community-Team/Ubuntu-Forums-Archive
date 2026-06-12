---
title: "File system check fails after installation"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by lofty00 on 2006-06-03
hello,

I've just tried installing ubuntu breezy badger (edit - correction it's dapper drake) after using debian for a long time. (It looks nicer and hopefully will save me some hassle and give better community support). The installation process itself went fine - it boots OK from the CD and the installation wizard ran without any bugs.

The problem is, when I reboot, the filesystem check fails. My filesystem is partitioned like this (from fdisk /dev/hda):

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/hda2            1217        3770    20515005    5  Extended
/dev/hda3            3771        8869    40957717+  83  Linux
/dev/hda4            8870        9729     6907950   83  Linux
/dev/hda5            1217        3128    15358108+  83  Linux
/dev/hda6            3129        3638     4096543+  83  Linux
/dev/hda7            3639        3770     1060258+  82  Linux swap / Solaris

I told it to use /dev/hda5 for /, /dev/hda6 for /var, /dev/hda3 for /local (which includes things like /home, /usr/local, etc, which is how I've had it set up before in debian), and /dev/hda7 for swap.

After rebooting for the first time from the hard disk, it goes to a root terminal and stops with a message like:

/: failed filesystem check - filesystem size is 320000 blocks, whereas device size is 150000 blocks. Either the filesystem or the partition table is likely to be corrupt.

I've tried rebooting again from the CD and using fsck to recover the filesystem (using -c -f flags - i.e. check for bad blocks and force all checks to be run). The filesystems I'm using all pass this check, but the same error happens again when I reboot.

Any help would be appreciated.

---

### Post by lofty00 on 2006-06-03
Update - I've now tried this:
- booting from the live CD
- manually creating the filesystems I'm installing to using mkfs
- rebooting and then installing with formatting the partitions.

The same problem is still happening. If anyone can help with this I'd appreciate it, as I can't use my machine properly until it's sorted (unless I go back to debian, which I would rather not do.)

---

### Post by Jamesia on 2006-06-10
I am also having a similar problem. While I was installing dapper, a notice came up saying my windows partition (fat32 to mix with linux) was a malformed partition. I know it's not... I'm using it now. But I continued the installation anyway. Now that it's installed, dapper stops booting at the filesystem check.

Any suggestions? 
I'm using ext2 if it helps.

---

