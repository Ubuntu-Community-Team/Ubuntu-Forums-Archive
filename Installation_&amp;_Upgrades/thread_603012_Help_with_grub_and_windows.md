---
title: "Help with grub and windows"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Stephen-I-M on 2007-11-04
I would like to get help getting windows to boot on my system. I just did a clean install of 7.10 on /dev/sda. Windows is on /dev/sdb1 and fills that whole drive. I am able to mount sdb1 manually without any problems.

sdb has one partition and it's all for windows. I tried putting the following into my menu.lst file:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fa3a5758-6af9-4350-8261-7f311bd8a9b1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fa3a5758-6af9-4350-8261-7f311bd8a9b1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1
```
If I choose windows xp, I just get a "Starting" message but no windows, Thanks.

Stephen

---

### Post by meierfra on 2007-11-05
Use "sudo gedit /boot/grub/menu.lst" to open "menu.lst" Then change your windows item to

title		Windows XP
root		(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader	+1

---

