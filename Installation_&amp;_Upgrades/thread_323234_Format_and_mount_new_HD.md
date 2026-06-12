---
title: "Format and mount new HD"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by Kim Ming Yap on 2006-12-21
I have install Ubuntu onto one HD. I have another HD which i want to use. Of course i have to mount this hard drive later. How do i format this new HD and mount it.

---

### Post by bernied on 2006-12-21
try gparted

---

### Post by Kim Ming Yap on 2006-12-21
can you tell me exactly how to do it cos' i am not familar with unix or linux?

---

### Post by bernied on 2006-12-21
All of these things have been explained before, search the forum. 

What you want to do is [possible applications to use in brackets - there are many more]
- create a partition on the disk (or two or more) [gparted, qtparted]
- create a filesystem on the partition(s) [gparted, mkfs]
- mount the partition(s) [you need to edit the /etc/fstab file]

Here's some useful bits of information.

[http://www.beginningubuntu.com/software_1.html](http://www.beginningubuntu.com/software_1.html)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
[http://www.die.net/doc/linux/man/man5/fstab.5.html](http://www.die.net/doc/linux/man/man5/fstab.5.html)
[http://www.die.net/doc/linux/man/man8/mount.8.html](http://www.die.net/doc/linux/man/man8/mount.8.html)

---

