---
title: "dual boot menu titles mixed up/transposed"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by kamikazepsi on 2010-05-02
Here's my boot menu:

linux image: /boot/vmlinuz-2.6.32-22-generic
initrd image: /boot/initrd.img-2.6.32-22-generic
linux image: /boot/vmlinuz-2.6.32-21-generic
initrd image: /boot/initrd.img-2.6.32-21-generic
memtest86+ image: /boot/memtest86+.bin
Windows Vista (loader) on /dev/sda1 
Windows Recovery Environment (loader) on /dev/sda2

Issue:

-When I select Windows Vista to boot into, it loads Windows Recovery

-When I select Windows Recovery, it loads the normal Windows Vista

-Sudo update-grub doesn't fix anything 

??? It's not a big deal but that's pretty weird.  Anyone else getting this?

---

