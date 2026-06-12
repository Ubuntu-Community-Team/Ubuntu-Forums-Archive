---
title: "installing grub problem (or rather booting ubuntu from it)"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by mez_ on 2008-11-28
I'm trying to boot an old ubuntu installation from a grub that i installed on an USB stick. I got the grub working, but when I try to boot my old ubuntu install from it I get: 

error 17 cannot mount selected partition

I copied all the necessary files that the menu.lst entries refer to from an old grub install on my hard drive (and all other files that werent created by the standard grub install just to be sure), and I tried changing the root (0,1) (where my old grub is) to (0,2) (where my ubuntu installation is) and to (1,0) (where the grub install on the USB stick is), and tried to boot from all of those configurations, with the same error.

my hard disk setup looks like this:
only 1 hard disk
partition 0: windows xp
1: old grub
2: old ubuntu installation

Why: I use a truecrypt encrypted windows xp so i cant load grub anymore. yes there are other work arounds but i want to do it like this. also, id like to learn how to set up grub on a usb stick properly and boot operating systems from it.

What my menu.lst file looks like:

```
default 0
timeout 30

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=f416fb1b-9142-4b43-a128-71d38df4b644 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=f416fb1b-9142-4b43-a128-71d38df4b644 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet
```

Thanks for helping

---

### Post by caljohnsmith on 2008-11-28
so are you booting the USB stick, and from that Grub menu trying to boot your old Ubuntu on your HDD? How about in your menu.lst using "root (hd1,2)" instead of "root (hd0,1)". If that doesn't work, then please post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

