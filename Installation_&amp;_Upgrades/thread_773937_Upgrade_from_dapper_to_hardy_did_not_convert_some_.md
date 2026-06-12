---
title: "Upgrade from dapper to hardy did not convert some fstab entries to UUID-style"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by wildbillnj1975 on 2008-04-29
I just upgraded from 6.06 dapper all the way up to hardy 8.04.  Went smoothly for the most part.  One thing that's still broken is my fstab.

I have a few entries which did not get converted from /dev/hda* style to UUID style.  Fortunately they are two partitions which I rarely use.  Here are my original and updated fstab files:

proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda2       /home           ext3    defaults        0       2
/dev/hdc1       /myth1          xfs     defaults        0       2
/dev/hdd1       /myth2          xfs     defaults        0       2
/dev/hda4       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


NEW:

proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=86b02715-09d0-45fb-96b4-ed5a4dace492 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=a6bde815-25e7-4378-911a-8927aefb680e /boot ext3 defaults 0 2
# /dev/hda2 -- converted during upgrade to edgy
UUID=de144a4c-9e92-492b-afae-f61a02c8b792 /home ext3 defaults 0 2
[B][COLOR="Blue"]/dev/hdc1       /myth1          xfs     defaults        0       2
/dev/hdd1       /myth2          xfs     defaults        0       2[/COLOR][/B]
# /dev/hda4 -- converted during upgrade to edgy
UUID=18014e24-348e-4283-9397-fcb6197b5f61 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hdc1 and /dev/hdd1 did not get converted.
Honestly, it's been so long since I opened this box, I forget if they are separate physical disks, but I believe they are.

There is no /dev/hdc1 or /dev/hdd1, and there are no /dev/sd* other than the four partitions that got converted OK.

I figure it must be that the new kernel is not recognizing the disk, which is weird because it had no problems in dapper.

Any ideas folks?

---

