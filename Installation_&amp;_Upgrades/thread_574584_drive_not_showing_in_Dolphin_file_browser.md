---
title: "drive not showing in Dolphin file browser"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by robertsaron on 2007-10-13
I Have mounted a hard drive in my /media folder.  I created a folder called storage. I am not able to see this folder in Dolphin, but can see it in Konqueror, and can see it in the media folder when browsing by command line.  I had to create the folder caled storage using command line at root, as dolphin and konqueror would not let me.

How do I get it so I can see this folder in the dolphn file browser? I am on tribe 5 of gutsy gibbons, using 32 Kubuntu version.

---

### Post by robertsaron on 2007-10-13
pasted below is a copy of my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=f074c511-5b9f-49cc-8c5b-09d1671ce88a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=3e341083-58d7-46db-b714-8b2d46fbb39e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc1       /home/aaron/storage     ext3    rw.user,auto,exec   0        0


It seems to be a permissions issue some how. Though if it is a permissions problem, how do I fix it? This shows that I even tried to mount it in my home folder. The folder storage shows there, but on reboot it does not automatically mount my sdc1 drive.

---

