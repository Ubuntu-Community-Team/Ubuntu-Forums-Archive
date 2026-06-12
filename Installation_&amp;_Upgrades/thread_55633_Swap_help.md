---
title: "Swap help"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by lebbyac on 2005-08-09
I have not my swap partition active, i create a partition in with fdisk in /dev/hda3
I nedd to know wath i must write in fstab file.

---

### Post by fng on 2005-08-09
here is a portion my /etc/fstab file :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdc1       /mnt/hdc        reiserfs defaults       0       2
....

```

/dev/hda1 is my swap-partition
Add a similar line in your /etc/fstab (replace /dev/hda1 with /dev/hda3 :))

---

### Post by kosmic on 2005-08-09
I'm not with my machine right now, so I can't tell the exact comands but do a 

man mkswap
man swapon
man swapoff

so you can learn how to configure the swap in your system :)

---

