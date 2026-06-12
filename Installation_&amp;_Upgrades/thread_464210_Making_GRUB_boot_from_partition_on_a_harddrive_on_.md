---
title: "Making GRUB boot from partition on a harddrive on PCI SATA controller"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by runesvend on 2007-06-04
Hey all

I'm trying to move my Ubuntu partition from one hard drive to another so I've copied my Ubuntu partition over to another partition with partimage and the Ubuntu Live CD.

Now my problem is how I get GRUB to boot from this newly created Ubuntu partition. Perhaps the problem lies in the fact that this faster hard drive is connected to my PC with a PCI SATA controller card. Ubuntu sees it fine and calls it sda1 but when I try to tell grub to boot from (hd1,2) it tells me there is no such hard drive. Does anyone have any ideas?

Thanks in advance!

---

### Post by louieb on 2007-06-05
Try the Reinstall Grub link in my signature. or the  [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/")
Probably going to have to modify the  /etc/fstab  file too. 
To get the uuid's of your partitions.
```
ls /dev/disk/by-uuid/ -l
```

---

