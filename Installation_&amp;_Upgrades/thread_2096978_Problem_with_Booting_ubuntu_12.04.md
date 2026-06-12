---
title: "Problem with Booting ubuntu 12.04"
date: 2012-12-21
forum: Installation &amp; Upgrades
---

### Post by dzudo on 2012-12-21
I have installed Ubuntu 12.04 LTS on my netbook Medion from Pendrive, all gone smoth but it is problem with booting, i have black screen and nothing happend, if I boot system again from pendrive than all is booting nice. I loggin and all work perfect. I swap to Ubuntu 10.10 netbook version in here all it works, install and then loggin, I try again version 12.04 and again this same problem. Can you help please.

---

### Post by Bashing-om on 2012-12-21
dzudo; Hi ! Welcome to the forum.

Right off hand I would say that grub (ubuntu's boot loader) is on the pen drive, rather than on the hard disk. Thus the pen drive has to be present to boot.
To see where grub has been installed run these terminal commands:
```
sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
```To identify all partitions/devices, with pen drive active:
```
sudo fdisk -l
```To install grub:
 ```
sudo grub-install /dev/sda
``` Assuming you desire grub to be installed on the first hard drive; And the partitioning is msdos scheme 

See these tutorials for more info:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

[INDENT]just try'n to help <== BDQ

[/INDENT]

---

