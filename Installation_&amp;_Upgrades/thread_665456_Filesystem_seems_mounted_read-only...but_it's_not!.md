---
title: "Filesystem seems mounted read-only...but it's not!"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by chris.simpson on 2008-01-12
Ubuntu 7.10 on a Dell Inspiron 531, dual-boot with Vista (sorry).

Booting goes fine until about 1/4 of the orange bar, when it reverts to text mode with the following:

```

* Checking root file system...
fsck 1.40.2 (12-Jul-2007)
Filesystem seems mounted read-only. Skipping journal replay.
Checking internal tree...finished
Reiserfs superblock in block 16 on 0x805 of format 3.6 with standard journal
Blocks (total/free): [appropriate numbers]
Filesystem is clean.
```
It then repeats the last 3 lines and carries on booting. There do not seem to be any problems with this, insofar as my root partition is *not* mounted read-only.

Here's my /etc/fstab. I've rebooted with everything except /dev/sda5 and /dev/sda6 deleted to confirm that it's an issue with the root or swap partitions.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=368a751d-1598-4188-8262-d114e2d0f929 /               reiserfs notail          0       1
# /dev/sda1
UUID=07D8-0104  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=1482E25D82E242BA /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=785AE7215AE6DAC0 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=ac796123-d28d-489b-822e-aeeb52291c98 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```

It doesn't seem to cause any problems, but I'd like to understand what's going on, and whether it may be a symptom of something serious. I'd appreciate anyone's help.

---

### Post by RegularSlinky on 2008-01-12
Hi, I'm not a Linux expert but I managed to partition a XP NTFS drive using Partition Manager successfully. Not sure if Reiser is a problem. Mine works with ext2.

---

### Post by chris.simpson on 2008-01-13
Well, reiserfs (which I'll admit I'd never heard of before) is what was recommended on the ubuntu install web page. I guess I'll carry on regardless and see what happens.

---

### Post by PmDematagoda on 2008-01-13
I use ReiserFS on my Ubuntu 8.04 system and I get the same message as well, as it does not seem to mean anything since there is no problem to be seen, I just ignore it and go on:).

---

### Post by chris.simpson on 2008-01-14
OK, thanks. But please PM me if your computer bursts into flame! ;)

---

### Post by PmDematagoda on 2008-01-14
> OK, thanks. But please PM me if your computer bursts into flame!  

Don't worry, I will, but if my PC ever goes up in flames it would be due to my processor instead of my hard drive:D.

---

### Post by kafiland on 2008-06-12
Same problem since 2.6.24.x

---

### Post by PmDematagoda on 2008-06-13
> **kafiland said:**
> Same problem since 2.6.24.x

If you wish to continue this support topic then please make a new thread instead of resurrecting one to do that.

This thread is closed.

---

