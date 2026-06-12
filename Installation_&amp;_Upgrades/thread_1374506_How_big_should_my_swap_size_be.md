---
title: "How big should my swap size be ?"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by oygle on 2010-01-06
After finding out that karmic does a default EXT4 on the install, I'm now doing a re-install and force it to EXT3.  Have come to the 'manual' side of partitioning, and I'm able to choose EXT3, but that leaves no room for swap. What mountpoint should I define for the primary partition.

How big should the swap size be ?

It's a 500Gb hard drive. The 'manual' part of the install says it is a 500105 Mb size, and 10884Mb used, that is, with just primary - /dev/sda1 defined.  I don't know what the 'used' space is ??

How big should I make the swap size please ?

Oygle

---

### Post by raymondh on 2010-01-06
> **oygle said:**
> 

How big should I make the swap size please ?

Oygle

My preference is 1x maximum installable RAM (in case you do max out the RAM).  That said, if my system is capable of installing 32gb RAM, I would make my swap 32gb.  That's my preference.

With a 500gb HD, 5gb is only 1% ;)


EDIT : Do you need assistance doing a manual install?  If so, post a screenshot of gparted to help visualize.  That or 

```
sudo fdisk -l
```

Regards,

Raymond

---

### Post by adam814 on 2010-01-06
There's no simple answer for that.  The old recommendation was twice your installed RAM (i.e. for 1GB RAM you had 2GB of swap space).

Some people still recommend that and some people use no swap space at all without problems.

If you intend to "hibernate" the machine you'll need at least as much as you have physical RAM to do it reliably.

As for the "used space" that's just how much filesystem overhead there is.  Some of those are superblock backups and some of that is reserved for the journal and IIRC some small percentage of ext filesystems are reserved for root.

---

### Post by Sef on 2010-01-06
Locked.  [Double Post]("http://ubuntuforums.org/showthread.php?t=1133719&page=27").

---

