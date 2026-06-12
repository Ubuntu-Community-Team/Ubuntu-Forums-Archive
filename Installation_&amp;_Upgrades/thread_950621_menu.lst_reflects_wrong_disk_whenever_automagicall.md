---
title: "menu.lst reflects wrong disk whenever automagically modified"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by anystupidname on 2008-10-17
I'm having difficulty understanding why an external USB storage drive that is not bootable is hd0,0 (/dev/sdb) and the internal SATA drive I boot from normally is hd1,0 (/dev/sda). Every time I let a kernel upgrade occur, it changes the entries in /boot/grub/menu.lst to hd0,0 which make it not bootable until I fix it manually... If anybody has any suggestions, they would be much appreciated!

menu.lst
```
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=8c5316a2-1f84-47ea-ab90-b424eebd9d1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=8c5316a2-1f84-47ea-ab90-b424eebd9d1f ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8c5316a2-1f84-47ea-ab90-b424eebd9d1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8c5316a2-1f84-47ea-ab90-b424eebd9d1f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title UNetbootin-partitionmanagerrev146
root (hd0,0)
kernel /boot/ubnkern noapic root=/dev/ram0 init=/linuxrc ramdisk_size=200000 keymap=us liveusb vga=791 quiet toram
initrd /boot/ubninit
boot

```

fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8c5316a2-1f84-47ea-ab90-b424eebd9d1f /               reiserfs notail,relatime 0       1
# /dev/sda5
UUID=70915f17-f612-472f-952c-698e8a57e43f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

###STORE### /dev/sda3
UUID=8b6ad4f3-31ce-4c73-b484-93e8a33e8b24	/store	jfs	defaults	0	1

###VM### /dev/sdb1
UUID=888d5a16-fe34-42b2-825b-49dfd81e12f4	/vm	jfs	defaults	0	1
```

---

### Post by ianhaycox on 2008-10-17
Not much consolation but I have the same problem. I have an old dapper/edgy/feisty updated install on one partition and hardy on another. Updating the kernel always messes up menu.lst and uses the UUID and root() of the old partition but the kernel names in the new partition.

I'd love to know why and how to fix it, preferably before I upgrade to Ibex.

---

### Post by anystupidname on 2008-10-30
This problem appears to be fixed in Ibex... (8.10)

---

### Post by C.S.Cameron on 2008-10-30
This also happened to me in the early days of 8.10 but seems to be fixed now.
Have not seen it in 8.04.
You could try unplugging your USB before doing an upgrade.

---

### Post by ianhaycox on 2008-11-11
As I feared I got bitten by this upgrading to Intrepid. Manually editing menu.lst during the updrade fixed my problem.

However, I did notice that I had a line,

```
# kopt=root=UUID=d1f2d712-0cad-48f7-84d8-46b03c647232 ro
```

in menu.lst with the UUID of my old partition. Changing to the correct UUID has fixed the problem on subsequent kernel updates.

---

