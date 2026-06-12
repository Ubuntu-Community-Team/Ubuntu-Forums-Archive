---
title: "Booting problem on RAID1"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by madcrock on 2006-06-06
Hello all,

I'm stuck with a problem booting xen 3.2 (2.6.16 kernel) on raid1, dapper drake. Original dapper server kernel boots fine.

my fstab configuration:

/dev/md0  /boot
/dev/md1 /
/dev/md2 swap

I created initrd with md and raid1 modules included.

When booting md1 and md2 devices are detected and mounted nicely, but the probem is with md0 (/boot) - the device /dev/md0 is empty file... fsck complains about that on boot and gives command prompt. 

Maybe anyone experienced similar problems? 

Thanks in advance,
Laurynas

---

