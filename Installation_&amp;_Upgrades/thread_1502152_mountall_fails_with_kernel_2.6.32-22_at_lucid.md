---
title: "mountall fails with kernel 2.6.32-22 at lucid"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by sv1jsb on 2010-06-05
Hello everybody,
I have upgraded at lucid from karmic.
I have a little peculiar setup. My root partition is on sda3
and I mount the following:
/usr -> /dev/sdb1
/var ->/dev/sdb2
/home -> /dev/sdb3
(sdb isn't really a SATA disk but a PATA).
When I boot with the new kernel 2.6.32-22 mountall
stops with error messages that /dev/sdb2 and /dev/sdb1 are not ext2 filesystems
(this message comes from fsck.ext4??-It's using a ext4 program to check for ext2??)
and cannot be mounted.
Of cource those are normal ext4 filesystems which are being mounted without any problems with the last karmic kernel 2.6.31-21 which is what I am using)

Is there a way around it?

Thanks in advance for any input,

Andreas

---

### Post by MasterZ on 2010-06-09
Hi, 

I've got the same behavior as you do, with kernel 2.6.32-22 I get errors (It's saying:"Serious error") while mounting my /home at startup. 
It's an ext4 filesystem for me, I tried to mount it manually as ext4/3/2 but no luck. 
When I try to run fsck it tell me that it cannot run and that it may be a zero size partition... (don't remember the exact msg though). 

I'm doing a backup just in case the disk has a real problem and I'm using the 2.6.32-21 kernel. 

I'll have a look on launchpad to see if someone else reported the problem there.

---

### Post by sv1jsb on 2010-06-10
Hi,  I am not sure what exactly was my problem but I am guessing that this kernel is missing something my system needs. I suspect it's the HD controller, it's a JMicron. So I downloaded the latest from kernel.org (2.6.34) and made one for my system. After that it works fine.  Hope that helps, Andreas

---

