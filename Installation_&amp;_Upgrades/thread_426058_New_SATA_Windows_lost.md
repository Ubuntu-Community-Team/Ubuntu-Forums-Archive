---
title: "New SATA: Windows lost"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by Bosonator on 2007-04-28
I recently installed a new SATA hard drive and installed Ubuntu first (I like the partition editor on the live CD best). I then installed Windows to a partition and got that going. Of course I had to use the live CD next time I wanted to use Ubuntu, replacing GRUB to the master boot record. I did that, but now only Ubuntu shows up in the GRUB list - Windows isn't there. Any fixes (I'm sure this is an easy one)?

---

### Post by Herman on 2007-04-28
Hello Bosonator
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1
``` You didn't say what hard disk and partition Windows is in, but if it's your first hard disk and first partition (standard), then you should be able to copy this entry and paste it to the bottom of your menu.lst file, either below the end of the debian automagic kernels list, or above the beginning of the automagic kernels list. Don't put it anywhere inside the automagic kernels list though. If you do, it will get deleted  every time Ubuntu gets a new kernel in an update.  :)

If you installed Ubuntu first, then Windows, Ubuntu would be in partition 1, and 2 would be an extended for your swap area (5), so that would make Windows number 3 I would guess. If that's the case change (hd0,0) there to (hd0,2) instead.
If you made more partitions, such as a separate /home when you installed Ubuntu, then Windows might be (hd0,3). 
If you need any help you should post the output from 'sudo fdisk -lu', then someone can give you exact, specific help. :)

Regards, Herman :)

---

### Post by Bosonator on 2007-04-28
Thanks, I'll try that for now, but isn't there any way to just tell grub to reinstall itself? I recall that it's capable of autodetecting all the OSes present on a computer, and that would be nice. A hack is great when necessary, but I try to avoid them if there's another way. Thanks Herman!

---

