---
title: "Label of external disk:changed to all capitals after upgrade"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by alobo on 2010-05-20
Hi!
I have an external disk (vfat) that had label "Transcend" under
ubuntu 9.04. After upgrading, the disk is now mounted
as /media/TRANSCEND (all capitals) which creates a big
trouble for the many scripts I have assuming /media/Transcend

I've changed the label using GParted, but even if I write "Transcend",
after I click Apply the label appears as "TRANSCEND"

I've checked the GParted support and they say that GParted writes
"Transcend" but blkid reads TRANSCEND.
([http://gparted-forum.surf4.info/view...d=23348#p23348](http://gparted-forum.surf4.info/view...d=23348#p23348))

Is there any way I can get my disk to be mounted as /media/Transcend again?

Thanks,

Agus

PS

This output might be relevant:
alobo@alobo-laptop:~$ sudo blkid
/dev/sda1: UUID="7074DF6774DF2F1A" TYPE="ntfs"
/dev/sda2: UUID="0ce7c849-ecfe-4593-90f4-a9c1ed69aeb4" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda4: UUID="4816-D9F2" TYPE="vfat"
/dev/sda5: UUID="27f7552d-d0bc-470b-a329-dbfacc2d8e3b" TYPE="swap"
/dev/mmcblk0p1: LABEL="CANON_DC2" UUID="1111-A131" TYPE="vfat"
/dev/sdb1: LABEL="EXCHANGE" UUID="606C-87A6" TYPE="vfat"
/dev/sdb2: LABEL="TRANSCEND" UUID="D661-7C91" TYPE="vfat"
alobo@alobo-laptop:~$ sudo vol_id
sudo: vol_id: command not found

alobo@alobo-laptop:~$ ls -l /dev/disk/by-label
total 0
lrwxrwxrwx 1 root root 15 2010-05-12 18:36 CANON_DC2 -> ../../mmcblk0p1
lrwxrwxrwx 1 root root 10 2010-05-12 19:47 EXCHANGE -> ../../sdb1
lrwxrwxrwx 1 root root 10 2010-05-12 19:47 TRANSCEND -> ../../sdb2

---

