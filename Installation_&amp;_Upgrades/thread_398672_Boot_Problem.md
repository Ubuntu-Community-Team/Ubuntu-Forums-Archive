---
title: "Boot Problem"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by tomus on 2007-04-01
I'm running ubuntu 86_64AMD on my acer aspire 5021.

Recently I have been trying to get the wireless working with ndiswrapper with limited success.  However, during this process I updated all my packages and got the latest kernel with headers

2.6.17.11

but now when I restart the boot splash screen gets stuck and it does not boot.  I therefore booted without the splash screen from GRUB and it came up with:

Kernel sync error. Aeee killing ....

I cannot get into the old kernel either.

How can I fix this I dont want to do a completely new install.

---

### Post by pradeepadapa on 2007-04-01
first of all is ur grub menu working or not, of not working u can first reinstall the grub from the live cd , then tell us if its working or not

---

### Post by tomus on 2007-04-01
GRUB works fine, I think it is a problem actually booting ubuntu.

---

### Post by pradeepadapa on 2007-04-01
is rescue mode working or not, if not working then tell us when the grub menu occurs just type 
" e " on either the rescue mode or on the main nd tell us what d u get

---

### Post by tomus on 2007-04-01
Rescue mode does not work either. Typing e on the GRUB menu gives:

-root (hd 0,3)
-kernel /boot/vmlinuz-2.6.17-11-generic root: /dev/hda4 ro quiet splash
-initrd /boot/initrd.img-2.6.17-11-generic
-quiet
-save default
-boot

---

