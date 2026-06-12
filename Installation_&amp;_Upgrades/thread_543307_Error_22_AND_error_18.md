---
title: "Error 22 AND error 18"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by rcrusk on 2007-09-04
As a complete neophyte to this game, I have probably just made a simple error but need help now.
I installed as directed by the many forum articles on installation with a LIve CD.
Everything loaded fine to the partition I had hoped for. But no go with the subsequent boot. I then used SuperGrub to fix the problem and since then I have had the Error 22 on the first selection for the dual boot and any other boot requests are an Error 18.

Some general info:
Dual SATA drives, no IDE
/dev/sdb1 XP
/dev/sdb6 Vista (seen in the boot option)
/dev/sdb9 Ubuntu (with a boot flag in the Gparted screen)
/dev/sdb10 linux-swap

find /boot/grub/stage1 = hd1,8 which I used to install the grub to the mbr.

Any suggestions for fixing this or do I reformat the lot and start again?

---

### Post by rcrusk on 2007-09-05
So I have an update:
I managed to boot into ubuntu with supergrub by using the "special boot": this switches the hard disk configuration and then boots.  So my SATA4 was seen as SATA3 and could then boot.  So obviously mt mapping is wrong but I don't know how to fix that.

My menu.lst looks like this:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=79ccc05c-d7c1-46fb-a67a-82b3ad7222a3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=79ccc05c-d7c1-46fb-a67a-82b3ad7222a3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=79ccc05c-d7c1-46fb-a67a-82b3ad7222a3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=79ccc05c-d7c1-46fb-a67a-82b3ad7222a3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Do I have to change the map to (hd1)(hd0)?

The other problem is that once I reboot, the HD switch will switch back to the original order so I won't be able to boot again.

Any help out there yet???

---

