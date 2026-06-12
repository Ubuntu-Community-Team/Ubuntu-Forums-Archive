---
title: "sharing /home with 2 linux and windows"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by gtludwig on 2006-10-15
Hello all,

I've decided to make my system dual (or triple) boot. I've patitioned my hard disk like this:

primary partitions
/dev/sda1	20Gb	ntfs	WinXP
/dev/sda2	10Gb	ext3	Linux
/dev/sda3	10Gb	ext3	Ubuntu Dapper x86_64
extended partitions
/dev/sda4	71Gb+
/dev/sda5	1Gb	linux-swap
/dev/sda6	70Gb+	fat32	shared WinXP and Linux

I've two 10Gb ext3 partitions. One for Dapper and the other for another linux, probably Slackware 11.0 32bits.

I want to mount in /dev/sda6 as my /home so my linux sees it as /home and my windows installations sees it as D:\. Below is my /etc/fstab. I've tried to put /home where it is /media/sda6 to see it it worked. It didn't. Now, /home can only be mounted in ext2, ext3 or raiserfs partitions?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Can it be done? If so, how?

Thanks!

---

### Post by Kateikyoushi on 2006-10-15
I would resize the 70GB fat partition to make space for an ext and mount the / home folder there.

With [this]("http://www.fs-driver.org/") driver you could read and write that partition from windows as well.

---

### Post by ansi on 2006-10-15
```
/dev/sda6    /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0  1
```
AFAIK, fat32 nothing knows about unicode. It is an advantage of NTFS. Remove ``utf-8'' above and try again.

So, keep in mind, that partition mounted as /home must contain directories about which your system knows.
e.g.: if for user ``gtludwig'' in /etc/passwd defined homedir ``/home/gtludwig'', that it has to be.

---

