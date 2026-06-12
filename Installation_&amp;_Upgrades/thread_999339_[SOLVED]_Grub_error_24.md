---
title: "[SOLVED] Grub error 24"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by Terraman on 2008-12-01
Dear Ubuntu friends,

I've installed Ubuntu 8.04 command line system in a Compaq Armada 1571 DM, 64 Mb memory, MMX, 200 MHZ.

After restarting I've got ERROR 24.

Does anyone know what does it mean and how to fix it?

Thank you in advance,

---

### Post by Diabolis on 2008-12-01
[http://users.bigpond.net.au/hermanzone/p15.htm#24_](http://users.bigpond.net.au/hermanzone/p15.htm#24_)

---

### Post by caljohnsmith on 2008-12-01
From the Grub manual:
> **Error 24**: Attempt to access block outside partition
This error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt filesystem on the disk or a bug in the code handling it in GRUB (it's a great debugging tool)
So that could be a sign that you have a corrupt partition table for instance. How about booting your Live CD, open a terminal (Applications > Accessories > Terminal), and please post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

---

### Post by betozombie on 2008-12-03
I have the same problem, here. 
but with 8.10
Hope you can help me.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9ba63a30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    41945087    20971520    7  HPFS/NTFS
/dev/sda2        41945715   230243579    94148932+  83  Linux
/dev/sda3       230243580   234436544     2096482+   5  Extended
/dev/sda5       230243643   234436544     2096451   82  Linux swap / Solaris

---

