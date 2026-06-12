---
title: "windows 10 autoupdate destroyed my dual boot"
date: 2015-12-05
forum: Installation &amp; Upgrades
---

### Post by abdullah6 on 2015-12-05
windows 10 autoupdated and destroyed my dualboot.
I have ubuntu 15.4 and it uses grub2

the only way to start it up is putting this in grub rescue:

set prefix=(hd0,msdos3)/boot/grub
  set root=(hd0,msdos3)
  insmod normal
  normal

by default the prefix is (hd0,msdos2)/boot/grub and the root(hd0,msdos2).

my problem is that I don't know how to make that change permanent.
boot repair does not work and grub-intall neither. when I try I say that the sector 32 is used by flexnet (i have no Idea what is that).

please help

---

### Post by grahammechanical on 2015-12-05
Posting the URL that Boot Repair gives will allow us to see for ourselves what Boot Repair is seeing.

This is telling Grub to look on partition 3 of the first hard disk for Grub's boot configuration files & to set partition 3 as the root.

> set prefix=(hd0,msdos3) /boot/grub
set root=( hd0,msods3)

But the default is pointing to partition 2. (hd0.msdos2) both for /boot/grub & to be root.

Have you tried?

```
sudo update-grub
```

Watch the printout. That will also be useful information to post here.

Regards.

---

