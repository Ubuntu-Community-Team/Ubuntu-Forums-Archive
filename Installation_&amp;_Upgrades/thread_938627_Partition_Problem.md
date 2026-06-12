---
title: "Partition Problem"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by willthebold on 2008-10-05
So I was getting rid of a partition using the installer, but then it started formatting my Ubuntu partition and I stopped it in the middle. Now Grub gives me an Error 17. From another installer menu, the drive that has Ubuntu on it has no file system. If I try to set it to Ext3, it says I have to format. Is there a way to get my info off the drive?

---

### Post by lemming465 on 2008-10-11
You may be able to get some of it back, but not all of it.  At this point you are in a forensic data recovery scenario, as much of the file system metatdata has been overwritten by the partial reformat.  Most of the data in the files is probably still present, however.  Try a tool like [foremost]("http://foremost.sourceforge.net/"), perhaps running from a live forensic CD such as [Helix]("http://www.e-fense.com/helix/")

---

### Post by Sef on 2008-10-12
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").  It can recover partitions.

---

