---
title: "Dual boot Ubuntu onto windows"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by cmol on 2007-04-23
Hello..

I need some advice with running a dual boot pc..
I have windows xp pro running on this machine (1,2 gHz intel).
The drives are parted as:

C: 30gb total - 12gb used - NTFS
D: 65gb total - NTFS
E: 55gb total - NTFS

All at the same disc

So if I install Ubuntu 7.04 on the "last 10gb" of the "C:", will I then be able to read and write to the D: and E: partitions, without re-partitioning them?..

---

### Post by pepsi_max2k on 2007-04-23
you wont be able to put it on C unless you resize it and create a new partition out of the unused space. and you'll be able to read ntfs partitions from ubuntu but not write to them. you can read/write to fat32 partitions, and any other linux ones, but windows can only access the fat ones. 

see [http://ubuntuforums.org/showthread.php?t=416981](http://ubuntuforums.org/showthread.php?t=416981) for more partitioning info.

---

### Post by cmol on 2007-04-25
> **pepsi_max2k said:**
> you wont be able to put it on C unless you resize it and create a new partition out of the unused space. and you'll be able to read ntfs partitions from ubuntu but not write to them. you can read/write to fat32 partitions, and any other linux ones, but windows can only access the fat ones. 

see [http://ubuntuforums.org/showthread.php?t=416981](http://ubuntuforums.org/showthread.php?t=416981) for more partitioning info.

Ok.. Thanks..

Why is it anyway that linux can't write to ntfs (and the other way around).. A feature like that would make it really nice for non ubuntu people to make dual boots..

: - )

---

