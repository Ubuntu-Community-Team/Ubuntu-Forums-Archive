---
title: "Fedora7 (grub2) Hijacked my Feisty (grub 1.5) install"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by ifthengoto on 2007-05-22
I currently have a main production Feisty install on my usb drive (hd1,0). I have some other Ubuntu versions on different partitions to test and "play" with.

I have no problems and used to just list them on my first menu.lst file and I could boot to all of them - including XP on my first hard drive.

Then - I decided to do a test install of Fedora 7 to check it out. I installed it to a new partition sdb9. When it asked during the install to install grub, I clicked yes much like you do when installing Ubuntu.

Now heres the thing!

When I now boot I go directly to the Fedora screen. I notice that before that I get a screen message saying "grub2". I used to get a message saying "grub 1.5".

If I add my Ubuntu entries to the menu.lst in Fedora I can the boot into any of my Ubuntu or Windows installations. Good!

The only thing is I would like to boot to my original Feisty production install at (hd1,0) and then choose from the items that I have added to the menu.lst to get to other test installs I have.

I have tried reinstalling grub using

```
find /boot/grub/stage1
root (hd1,0)
setup (hd1)
```which completes successfully, but I continue to get the Fedora grub2 splashscreen at  start up. 

Does anybody have and ideas how I can get grub2 to recognize my Feisty install as the first on the menu.lst?

(I see that grub2 is now available in the repos but I have not installed it because it says "alpha").


```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        9725    78083932+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1912    15358108+  83  Linux
/dev/sdb2           20398       30401    80357130    5  Extended
/dev/sdb3            6375       19122   102398310   83  Linux
/dev/sdb4           19123       20397    10241437+  83  Linux
/dev/sdb5           30214       30401     1510078+  82  Linux swap / Solaris
/dev/sdb6           30026       30213     1510047   82  Linux swap / Solaris
/dev/sdb7           20398       21672    10241374+  83  Linux
/dev/sdb8           29838       30025     1510078+  82  Linux swap / Solaris
/dev/sdb9           21673       21685      104391   83  Linux
/dev/sdb10          21686       29837    65480908+  8e  Linux LVM

Partition table entries are not in disk order

```

---

### Post by ifthengoto on 2007-05-22
Resolved - sometimes its the most simple things.

root (hd1,0)

But

setup (hd0)

---

