---
title: "gparted doesn't recognize partitions."
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by Ranny1 on 2007-05-16
Hi everyone,
I just started my experience with ubuntu, after working with a dual boot (red hat, then mandriva and noe suse).
I am trying to "replace" the suse on my dual boot Fujitsu laptop, but the gparted does not recognize any partition whatsoever (I have ntfs for win, 2 FATs, 2 ext2 and 1 swap, and suse 10.1 working well as dual boot).
The only response I get from the partitioner is "unallocated", using it alone as well as while trying to install.
The system does recognize the partitions and can view them and the contents as well, but...
Is there a quick solution for that? I really like to switch to ubuntu, at last...
Thanks,
Ranny.

---

### Post by monti on 2007-05-25
You can probably work around your problem by using TestDisk, look here: [http://ubuntuforums.org/showthread.php?p=2486121#post2486121](http://ubuntuforums.org/showthread.php?p=2486121#post2486121) 

The bug is located in gparted's subsystem, libparted: [http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14](http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14)

---

