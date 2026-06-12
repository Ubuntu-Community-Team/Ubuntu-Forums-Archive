---
title: "gnu fdisk vs util-linux"
date: 2009-01-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-07
Hi all, 
       Has anybody done any benchmarks or seen the differences between gnu-fdisk  and util-linux package?

I have installed gnu-fdisk and these are the changes that gnu-fdisk has done as far as util-linux I understand. 

```


/sbin/fdisk
diverted by gnu-fdisk to: /sbin/fdisk.distrib

/sbin/cfdisk
diverted by gnu-fdisk to: /sbin/cfdisk.distrib

/usr/share/man/man8/fdisk.8.gz
diverted by gnu-fdisk to: /usr/share/man/man8/fdisk.8.gz.distrib

/usr/share/man/man8/cfdisk.8.gz
diverted by gnu-fdisk to: /usr/share/man/man8/cfdisk.8.gz.distrib

```

There is some discussion on the same at [http://lists.alioth.debian.org/pipermail/parted-devel/2008-December/thread.html#start](http://lists.alioth.debian.org/pipermail/parted-devel/2008-December/thread.html#start)

Comments are welcome.

---

