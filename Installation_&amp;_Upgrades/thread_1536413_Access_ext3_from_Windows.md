---
title: "Access ext3 from Windows"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by yc2 on 2010-07-22
Hi,

I run Lucid on ext3. I really miss not being able to reach Lucid from my dual boot Vista.

I have installed the latest [fsdriver]("http://www.fs-driver.org/"). I have also tried this:
[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)
which does not work. (Is it because fsdriver is still in the system?)

I also tried these methods but to no avail.
[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

The problem seems to be related to fsdriver not being able to handle ext3 with Inode size = 256

Going back to ext2 for only the home partition seems complicated?

Please give advice.

Thanks.


EDIT:
I apologize if I post in the wrong category.

---

### Post by yc2 on 2010-07-22
Good news!

This works fine:
[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)

I don't know if it was because I hadn't uninstalled fsdriver properly, but after a new uninstall/install cycle this driver works fine.

Sorry for maybe sounding negative from the start, but when I went to ext4 I also had to skip partimage and use Clonezilla. Partimage is a perfect program, IHMO. I tried to restore twice with Clonezilla ("fool proof" clicking interface). Both times Clonezilla overwrote my MBR. Ubuntu partitions could not be restored. Had to fix with fixboot, fixmbr. Fortunately I had other Ubuntu data backup.

I therefore had to make fresh install of Lucid and chose ext3 for Lucid this time. fsdriver still didn't work. So much trouble. It now seems all solved since this seemingly works:
[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)

All trouble compensated by how well Lucid has worked in my box from day one.

---

