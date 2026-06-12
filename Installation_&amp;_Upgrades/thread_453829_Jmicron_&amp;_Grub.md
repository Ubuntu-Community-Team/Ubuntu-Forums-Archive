---
title: "Jmicron &amp; Grub"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by dkarko on 2007-05-24
Hi, i have a P5B-VM and the hdd with the operating systems is an IDE, so connected to Jmicron controller (Jmicron bios version 1.06.63 so supposingly grub is supported).
The harddrive has 4 partitions and i use Vista bootloader, however in the setup process i changed the linux partition to active so i can put grub there temporarily.
First of all, Feisty live cd always failed to install, due to grub.. No matter the partition or MBR it returned fatar error! I even tried to chroot into the installed bootless system and set grub manually, no luck. So i tried the alternate cd, grub failed again but lilo installed with no error (but had problems there too on every boot)
So with the system set up with lilo i tried to make grub work.
Thing is no matter what i did, any root disk i gave it, it would deny to work.
find /boot/grub/stage1 always reported error 15.

here's the device map (it looks correct to me, linux is installed in sdb 3d partition)
```
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

I gave up and stayed with lilo. BUT funny thing is that lilo manages to boot randomly (once per 3 tries.... sad), again when it fails it says something about not being able to mount or something. 
Anyway, i set the first partition back to active and made a lilo disk.
What is the case? To my knowledge jmicron is a widely used controller in  965 chipset boards.

I was reading that jmicron used to have a problem with grub and linux but supposingly all this is solved in jmicron bios 1.06.53 and kernel 2.6.18 .

---

