---
title: "/home partition is not mounted"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by LeXz on 2008-05-26
Hello, I've finally decided to switch from 7.10 to 8.04.
I've made a fresh install, and when the system booted, I saw that /home partitions is not mounted (sda6 in my case), desktop is default etc, and /home is on the system partition.

My /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=38f27b2f-7d2e-424c-add0-e40791f247f3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=0220aaed-f969-460c-bc97-f646c3ae326e /home           ext3    relatime        0       2
# /dev/sda8
UUID=9483-F69B  /media/stuff    vfat    utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=97c0c64c-b1ce-4083-a52e-fe8e1475b21f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by louieb on 2008-05-26
Thats curious its listed in the fstab listing.  Why do you think sda6 did not get mounted on /home?

To be sure run the** mount** command.  (mount with no options will list what is mounted and where).

Only thing I can think of is a UUID problem. run the** blkid** command and compare the UUIDs listed with the one in fstab and  fix as needed.

---

### Post by LeXz on 2008-05-26
That was UUID problem, sorry for bothering :P
Everything's fine now. :)

---

