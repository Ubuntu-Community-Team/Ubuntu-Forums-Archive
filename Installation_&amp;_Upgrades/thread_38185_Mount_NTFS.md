---
title: "Mount NTFS"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by Xanthous on 2005-05-30
I have 3 partitions on my HD, which used to be win2000.  I installed Ubuntu on one partition, but the other 2 have lots of data and are NTFS.

I was able to mount one drive, and now some time latter I attempted to mount the second one, but it gives the following error:

```
root@ubuntu:/home/dna # sudo mount -a
mount: mount point /media/dv does not exist

```

Following is how I have the config file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5       /media/dv       ntfs    umask=0222      0       0
/dev/hda6       /media/ang      ntfs    umask=0222      0       0
```

What am I doing wrong, and how can I get the second partition to read?

---

### Post by mtron on 2005-05-30
did you create the folder for your mountpoint?

in terminal type:
sudo mkdir /media/dv

and then
sudo mount -a

---

### Post by Xanthous on 2005-05-30
Somehow, I must have skipped that step.  

Thank you, following your instruction solved the problem, and it works.
 ;-)

---

