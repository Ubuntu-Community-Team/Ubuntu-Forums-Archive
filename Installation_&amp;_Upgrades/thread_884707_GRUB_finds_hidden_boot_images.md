---
title: "GRUB finds hidden boot images"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by bjourne on 2008-08-09
I have a really strange problem with GRUB. When I boot GRUB lists the
following kernels:

2.6.24-19-generic
2.6.24-19-generic (recovery mode)
2.6.22-14-generic
2.6.22-14-generic (recovery mode)
2.6.20-16-generic
2.6.20-16-generic (recovery mode)
2.6.17-11-generic
2.6.17-11-generic (recovery mode)
2.6.17-10-generic
2.6.17-10-generic (recovery mode)

The weird thing is that "ls -l /boot/vmlinuz*" lists the following
files:

/boot/vmlinuz-2.6.22-14-generic
/boot/vmlinuz-2.6.24-16-generic
/boot/vmlinuz-2.6.24-19-generic

That is, the 2.6.17-10, 2.6.17-11 and 2.6.20-16 kernels aren't even
installed! I have also verified that dpkg -l does not list them
either. And /boot/grub/menu.lst also only lists 2.6.24-19, 2.6.24-16
and 2.6.22-14. So how grub is able to find and boot from kernels that
does not seem to exist is beyond me.

This might have something to do with some weird lvm2 thingy that I have installed.

---

### Post by bjourne on 2008-08-09
It seems like GRUB is reading all my kernels from /dev/mapper/sda1.

```

sudo mount /dev/mapper/sda1 /mnt/sda1
ls /mnt/sda1
...
initrd.img-2.6.17-10-generic
initrd.img-2.6.17-11-generic
...

```
Voila! That is the real location from where GRUB loads the vmlinuz and initrd files. Very strange that that partition isn't mounted at /boot when Ubuntu starts as it should be.

---

