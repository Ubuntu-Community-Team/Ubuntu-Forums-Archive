---
title: "Ubuntu 7.10 on SanDisk Solid State Drive (SSD)"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by zoniq on 2008-03-03
I'm currently trying to install Ubuntu on a x86 unit with a SanDisk Solid State Drive (SSD). The disk has a size of 16GB, but the Ubuntu installer only detects it as 8.5GB. And also when I want to partition it I get an error message and can't continue.
A MythDora installation however works flawlessly.

Did anyone else had have these issues before? Any suggestions?

---

### Post by Tito1337 on 2008-03-12
I'm not the only one \\:D/

I can give more details. I'm running on a new Dell Latitude D430 with a 32GB SanDisk SSD UATA 5000.

First of all, Windows works great (you're right, Windows never works great...) on this SSD. The Install CD of Windows also recognize and can part/format it.

But on the Ubuntu Live CD it seems to be different... Ubuntu can mount the multiple partitions and read/write it. The problem is when you want to modify the partitions.

Gparted detects a drive of **-8589999616.00 B** (i.e. -8GB)... A negative value! It also shows only a non-allocated area of 512B. When I tried to create a new partition gParted aked to create a partition table but failed.

So I've tried fdisk but he says "incapable de repérage" (sorry, it's french...it means something like "incapable of locating").

Any idea?

---

### Post by Tito1337 on 2008-03-13
Help, please. :(

---

### Post by Tito1337 on 2008-03-15
I searched a bit this saterday...

Like many other drives, my SSD has a Host Protected Area. Here is what I can see during boot (without splash) of the live CD
```
ata1.00: Host Protected Area detected
current size: 61734911 sectors
native size: 61734912 sectors
ata1.00: native size increased to -16776960 sectors
```
Here is the error !

So, how do I correct that?

---

### Post by zoniq on 2008-03-17
Tito: Can you maybe fill in a bug report. I assume that no one who can fix it will read this thread here.

---

### Post by Tito1337 on 2008-03-19
I've successfully installed ArchLinux.

Thanks everybody

---

