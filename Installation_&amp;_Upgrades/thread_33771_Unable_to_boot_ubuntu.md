---
title: "Unable to boot ubuntu"
date: 2005-05-12
forum: Installation &amp; Upgrades
---

### Post by jaypeasy on 2005-05-12
Just installed ubuntu and have been unable to boot the os. The following error messages appear on the screen:

```
PCI: Cannot allocate resource region 3 of device 0000:05:00.0
audit (1115898403.216.0): initialized
Starting Ubuntu...
pivot_root: no such file or directory
/sbin/init: 428: cannot open /dev/console: no such file
kernel panic - not syncing: attempted to kill init
```

My hardware setup is:
AMD 64 3200+
Chaintech vnf4 ultra - nforce4 socket 939 motherboard
Geforce 6600GT PCIe graphics card
Seagate SATA 100 hard disk

---

### Post by defkewl on 2005-05-12
Would this have got to do with /etc/fstab and /boot/grub/menu.lst ? CMIIW

---

### Post by jon21 on 2005-05-12
I have a very similar problem.  Exactly the same error messages, except no PCI message as you have at the top of your log.

My system:
Dell Precision 530
30Gb SCSI disk
nVidia Graphics Card

Ubuntu 5.04 was installed and working perfectly on a small partition of the disk.  I attempted to re-install fresh and use the entire disk for Ubuntu.

---

### Post by jon21 on 2005-05-13
After much study/learning about grub, I fixed my install so it boots.

All that needed to be done was to fire up a Live CD Ubuntu and use it to edit my /boot/grub/main.lst file on my hard disk install of Ubuntu.  Had to mount the hard disk using mount -t ext3 /dev/sda1 /test (/test for example).

I changed /dev/sde1 to /dev/sda1 in /boot/grub/main.lst and that fixed my booting problem.

Why did Ubuntu install use /dev/sde1 instead of /dev/sda1?  I don't know, but it may have to do with my system having a multi-memory card reader installed, thus creating extra "drives" that the ubuntu install may have seen as available for some reason.  A bug worth fixing I would say.

Hope this is helpful to others.

---

### Post by Rehevkor on 2005-07-22
I ran into this error after using the Ubuntu Update Manager to install a new kernel update, and upon editing the menu.lst file I found that GRUB was looking for the new kernel on hda3. My Ubuntu install is on hda2.

Changing the reference fixed the problem, and now I can boot normally. Thanks!

---

### Post by drizzt on 2006-02-01
Is it possible to boot via kernel parameters without modifying "menu.lst" to not mount the device with the problem?

---

