---
title: "BTRFS Filesystem"
date: 2012-08-05
forum: Installation &amp; Upgrades
---

### Post by som1special2 on 2012-08-05
I'm always looking for the new thing with Distro's and wanted to try BTRFS. I have read that it is better for SSD's as it does not journal or record metadata. I currently use JFS for that reason.

The other day I tried installing and LMDE on a 60GB SSD drive with BTRFS and the following partitions:

/boot
/root
/home

Upon reboot I was issued an error shown here:

[IMG]http://i1232.photobucket.com/albums/ff366/som1special2/IMAG0088.jpg[/IMG]


Has anyone encountered this and if so, how can I fix it?

Thanks in advance!

---

### Post by oldfred on 2012-08-05
Not sure what is happening.

But Ubuntu runs fsck every 40 or 60 reboots or if file system seems to have issues. But fsck is only for ext2, ext3 & ext4 family of formats. Not sure it then it has a way to change what file repair system to periodically run or it is supposed to do that automatically and yours is not corrected?

Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)
Tuning Solid State Drives in Linuxcheckbox ssd
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

---

### Post by som1special2 on 2012-08-05
BTRFS does not seem to be supported in GRUB. That may mave something to do with it. I did eliminate it from /boot and used ext4 with the same outcome above when using /root btrfs & /home btrfs.

---

