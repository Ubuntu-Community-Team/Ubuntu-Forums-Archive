---
title: "windows 7 borked  partitioning"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by dougleduck on 2011-01-01
I attempted to install windows 7 to the partition where vista was installed.

The install failed, think it's a dodgy burn, and obviosuly took grub with it. 

However it's also somehow screwed up the partitioning of an extended partition where instead of two ubuntu's, a partition for my media files and test partition for chrome all is left is a big chunk of 'unallocated' and swap.

I found a recovery tutorial [here]("https://help.ubuntu.com/community/DataRecovery#GNU%20Parted") but the instructions are little vague.

Thanks for any help.

---

### Post by wyliecoyoteuk on 2011-01-01
[Parted Magic]("http://distrowatch.com/table.php?distribution=partedmagic")is what you need.
boot from the CD and use testdisk

---

### Post by oldfred on 2011-01-01
Some more links to testdisk:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by dougleduck on 2011-01-01
I managed to get testdisk working (afer realising i had to enable the right repos and install using live CD) and found a decent walkthrough. I'm now back to the much more familiar, error 15 file not found from grub :).

Home straight now...

Thanks for the help.

---

