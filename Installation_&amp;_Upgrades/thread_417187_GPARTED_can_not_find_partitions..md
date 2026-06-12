---
title: "GPARTED can not find partitions."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by hopestorm on 2007-04-21
I reinstalled my windows.
However, after I boot up from LiveCD...and then run Gparted, and it told me the whole disk is unallocated...

But I can Mount my Linux partitions using "Mount" command.

what's going on??

---

### Post by json684 on 2007-04-21
I have the same problem. I boot up fine into Windows, and Edgy. I was planning on a reinstall with Feisty. But the install DVD doesn't see my partitions. And using gparted liveCD also doesn't see them. The disk is just unallocated space. Please help us out.

---

### Post by monti on 2007-05-25
You can probably work around your problem by using TestDisk, look here: [http://ubuntuforums.org/showthread.php?p=2486121#post2486121](http://ubuntuforums.org/showthread.php?p=2486121#post2486121) 

The bug is located in gparted's subsystem, libparted: [http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14](http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14)

---

