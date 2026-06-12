---
title: "Paartition to upgrade"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by reb68 on 2007-01-27
I am trying to upgrade with the iso I burned a week ago or so. When I do install on the ver. 6.10 and get to manually partition this is what I have.
/home         39G    partition 1/disk IDE/ATA (Primary)(hda1)
/                 34G    Partition 3/disk IDE/ATA (Primary)(hda3)
/windows     10G    Partiton 1 /disk IDE/ATA (Primary)(hdb1)
swap            1G    Parition 2 /disk IDE/ATA  (Primary)(hda2)

Then I get the ERROR:
No root file system
FAT andNTFS File Systems may not be uesd on File Systems (/./boot/home/usr/etc.
It is usually best to mount them somewhere under /media
____________________
What do I do now? I am partitioning manualy because I do not want to format and lose my existing data.
Thanks
Dick

---

### Post by kingmonkey on 2007-01-27
It seems your trying to use FAT or NTFS as a filesystem for / .

When upgrading you usually reformat / and leave /home /windows as it is.

---

