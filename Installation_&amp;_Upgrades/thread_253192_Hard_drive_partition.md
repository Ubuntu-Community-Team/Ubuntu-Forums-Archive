---
title: "Hard drive partition"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by zapper on 2006-09-07
Hi,
I just installed ubuntu and i have 2 partitions on my hdd. One is a 15 GB / drive and other one is a 60 GB drive mounted on /files .
Both the drives are ext3. However the 60 GB drive is not accessible for normal user and only root is able to read from or write on it.
My fstab file looks like this :

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /files          ext3    defaults        0       2       umask=0 0 0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


```

Please tell me how to make /files partition accessible to all users.

---

### Post by Herman on 2006-09-08
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /files          ext3    rw,user        0       2       
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
``` Try changing your /etc/fstab entry to look like this. If it still doesn't work, try entering the following code in a terminal and see if it helps you,
```
sudo chmod -R 777 /files
``` Regards, Herman :D

---

### Post by zapper on 2006-09-08
Yeah.. figured that out.. thanks anyways..

---

