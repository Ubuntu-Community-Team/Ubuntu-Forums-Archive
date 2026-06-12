---
title: "Grub2 Custom menu items"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by mathgeek2000 on 2011-02-23
Hi All,

I need some help with my Grub2's '40_custom' menus -
I have Ubuntu 10.10, and some extra Linux ISO based Utilities in the custom menus.
I'm Trying to add the UBCD (Universal Boot CD v. 5.0.3) but it needs memdisk --

Here's the issue, I need to put the ISO files on the third partition, due to space issues:
  /home or (hd0,3) --> /SystemRestore.iso  , /PartedMagic.iso , and so on:
   --> Under normal use: UBCD is in:  -->  /home/ubcd503.iso

Here Parted Magic is loaded, and it finds the proper loopback files
I can even have both 5.9 and 5.10 of Parted Magic.

```
menuentry "pmagic-5.10.iso" {
search --set -f "/pmagic-5.10.iso"
loopback loop "/pmagic-5.10.iso"
linux (loop)/pmagic/bzImage uuid=5296ac94-191e-4e55-bd06-e868e0a5ccfb edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=788 loglevel=0 max_loop=256 livemedia noeject keymap=us
initrd (loop)/pmagic/initramfs
}

```

But here:

How do I modify the code below to say memdisk is on the 1st Boot Partition, with the grub.cfg files
  /boot/memdisk and /boot/grub/grub.cfg  where /boot is: (hd0,1)

But ubcd is on the 3rd partition:
  /home/ubcd503.iso where /home is (hd0,3) ?

```
menuentry "UBCD 503 with MEMDISK" {
  linux16 /memdisk iso raw
  initrd /ubcd503.iso
}

```

I have one drive sda: (sda1 - /Boot, sda2 - Slash(root), sda3 - /Home, sda4 - /Swap)

---

### Post by mathgeek2000 on 2011-02-24
Ok,

So I may have found part of my solution:

```
menuentry "hdt-0.3.6" {
   linux16 /memdisk
   initrd16 (hd0,3)/hdt-0.3.6.img
}
```

With the above code, 'Hardware Detection Toolkit' extracted from the UBCD ISO image is on my /home partition where I want it, and memdisk is on /boot. This works with a few other elements as well.
--
But I'd like to run the UBCD as if it were a CD I booted off of, and start with that menu - rather than build my own. and extract the pieces I need.

---

