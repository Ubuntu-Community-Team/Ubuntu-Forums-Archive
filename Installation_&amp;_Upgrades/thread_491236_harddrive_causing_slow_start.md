---
title: "harddrive causing slow start"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by Cam1223 on 2007-07-03
i have fiesty 64bit and its always taken ages to boot. there was a bootlog somewhere and i also looked at the boot with out the splashscreen once and it takes like 10 seconds in the beginning doing sumthing with one of the harddrives and it says error bad superblock and it keeps saying that over and over for like 10 seconds or so. I forgot where linux saves the bootlog, im sure one of you guys know and i'll post it. i have 2 harddrives one is really old and has nothing on it yet (it will soon) and the other is the one with linux and xp and everything else. when i saw the bad superblock errors it said hdb1 (the old hdd) so i took hdb1 off the fstab but this has not helped because it is still doing the same thing.

heres the fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=aedf3dee-b895-43d5-9c78-babb7b46dcbd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=23a32cd8-f1c5-485b-97e0-cfc7bf1c77f4 /home           ext3    defaults        0       2
# /dev/hda1
UUID=2A886BD0886B98D9 /media/Windows     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/hda5
UUID=a5e5010b-7684-46bd-93be-3e7eb4bb2de4 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```


i have heard of linux systems that boot in 20-30 seconds but mine takes about a min or two...5 min if it hits one of thoes checks ugh....

---

