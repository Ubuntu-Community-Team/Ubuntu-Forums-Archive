---
title: "Can I change GRUB to remove 1 HDD"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by pref-at-laval on 2007-03-11
I installed 6.06 in a machine with 2 drives. 1 200 Gig IDE with an old XP partition and 1 SATA 500 Gig brand new drive. During installation I indicated to use the SATA drive only. When I tried to remove the IDE drive, Ubuntu won't boot. Here is the content of /boot/grub/menu.lst (from the SATA drive):

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Here is the content of /boot/grub/device.map:

(hd0)	/dev/hda
(hd1)	/dev/sda

What I would like is for Ubuntu to boot even if the XP drive is not in the machine. Can this be done ?

---

### Post by lha on 2007-03-11
> **pref-at-laval said:**
> 
What I would like is for Ubuntu to boot even if the XP drive is not in the machine. Can this be done ?

Yes. Grub got installed on your old IDE drive, so you have to install it on your new drive. There are many threads in these forums that describe a variety of ways to (re)install grub.

---

