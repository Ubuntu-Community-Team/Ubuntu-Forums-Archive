---
title: "Mount Hard Drive"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2007-10-21
Here is my Fdisk info, What exactly do I add to my Fstab to make the drive work? Ubuntu messed up and I had to re-install and the data is still there and I need it.

Here is my fdisk info, what do I change or add? Thanks so much!

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot Start End Blocks Id System
/dev/hda1 1 4293 34483491 83 Linux
/dev/hda2 6883 7296 3325455 5 Extended
/dev/hda3 * 4294 6882 20796142+ 83 Linux
/dev/hda5 6997 7296 2409718+ 82 Linux swap / Solaris
/dev/hda6 6883 6996 915642 82 Linux swap / Solaris
Partition table entries are not in disk order
elliott@elliottlaptop:~$

P.S. I am Terminal Impaired so make it simple Please

---

### Post by confused57 on 2007-10-21
> **dontgetshocked said:**
> Here is my Fdisk info, What exactly do I add to my Fstab to make the drive work? Ubuntu messed up and I had to re-install and the data is still there and I need it.

Here is my fdisk info, what do I change or add? Thanks so much!

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot Start End Blocks Id System
/dev/hda1 1 4293 34483491 83 Linux
/dev/hda2 6883 7296 3325455 5 Extended
/dev/hda3 * 4294 6882 20796142+ 83 Linux
/dev/hda5 6997 7296 2409718+ 82 Linux swap / Solaris
/dev/hda6 6883 6996 915642 82 Linux swap / Solaris
Partition table entries are not in disk order
elliott@elliottlaptop:~$

P.S. I am Terminal Impaired so make it simple Please
Please post your current fstab:
```
gedit /etc/fstab
```
Which partition is the working Ubuntu and which partition is the one that you want to recover data from?

---

### Post by dontgetshocked on 2007-10-21
Fstab;

elliott@elliottlaptop:~$
sudo fdisk l
Password:
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot Start End Blocks Id System
/dev/hda1 1 4293 34483491 83 Linux
/dev/hda2 6883 7296 3325455 5 Extended
/dev/hda3 * 4294 6882 20796142+ 83 Linux
/dev/hda5 6997 7296 2409718+ 82 Linux swap / Solaris
/dev/hda6 6883 6996 915642 82 Linux swap / Solaris
Partition table entries are not in disk order
elliott@elliottlaptop:~$

---

### Post by confused57 on 2007-10-21
Copy & paste the command I gave you in my earlier reply in a terminal, then post the output.  You reposted fdisk, not fstab.  Are you wanting to recover data from the "nonworking" Ubuntu, or are you wanting to try booting it?

---

### Post by dontgetshocked on 2007-10-21
Just wanted to recover the data, but thanks anyway , I scrapped the thing and re-installed
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remountro
0 1
/dev/hda6 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by confused57 on 2007-10-21
If you ever need to mount a linux partition in the future, here are a couple of excellent guides:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

See the mounting linux sections in both links.

---

