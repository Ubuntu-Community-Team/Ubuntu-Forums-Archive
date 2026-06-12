---
title: "inode size inconsistencies in Intrepid"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by george293 on 2008-11-02
Hi, Installing  a fresh 8.10 results in inode size of 256 bytes. Once installed, the value cannot be changed. 
An inode size of 256 breaks just about every windows package wanting to access ext3 filesystems and, while not breaking it, makes it practically impossible to use ext3 partition back-up sofware running on Windows.
However, upgrading from 8.04 to 8.10 leaves the inode size as 128 avoiding all the above problems and more.
My questions are: why change the inode size in the first place, since only new Ubuntu users can take advantage of it (whatever that advantage is!) and why not make the inode size configurable as 128 or 256 when the partitions are formatted so that users depending on Windows s/w can continue using it?
Many thanks

---

### Post by Svenstaro on 2008-11-09
I ran into this and the problems it caused a few hours ago. And spend a few hours finding out what was wrong. Very annoying indeed.

---

### Post by howefield on 2008-11-09
That's interesting, must be why I'm having problems with backups using True Image which after 8.10 install complains about errors on the disk and will only do a sector by sector backup, which it does but results in a huge file size.

---

### Post by giosico on 2008-12-03
My fresh install of XP and Ubuntu 8.10 can no longer share the same home drive via ext2ifs aka fs-driver.org.  Ugg.

Am I really going to have to re-install again? :)

And why the change?

Anyone? Bueller?

---

### Post by caljohnsmith on 2008-12-03
Try using [Ext2FSD]("http://sourceforge.net/projects/ext2fsd") instead of your ext2IFS program; the Ext2FSD program supports the new 256 byte inode size ext3 partitions. :)

---

