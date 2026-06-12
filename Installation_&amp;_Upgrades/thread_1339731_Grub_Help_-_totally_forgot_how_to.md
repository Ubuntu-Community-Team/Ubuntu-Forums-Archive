---
title: "Grub Help - totally forgot how to"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by jwei45 on 2009-11-27
I lost my USB that had GRUB perfectly installed on it a few days back and I have no idea how to install it again. I totally forgot.

So I download winGrub and installed it to my usb

I am trying to just test a boot menu and here is my menu.lst

title Backtrack 3
root (hd0,0)
kernel /btboot/boot/vmlinuz
initrd /btboot/boot/initrd.gz ramdisk_size=6666 root=/dev/ram0 rw chexpand=256 load=cubez autoexec=xconf;cubez;startx

But whenever I test it with MobaLive USB, i get an error

Try (hd0,0):extended ir non-MS:skip

Any help please?

---

