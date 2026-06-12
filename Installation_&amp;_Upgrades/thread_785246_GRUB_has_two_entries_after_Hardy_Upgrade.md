---
title: "GRUB has two entries after Hardy Upgrade"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Umang on 2008-05-07
Hi!
I upgraded to Hardy using the alternate CD. Almost everything is fine, (I'm sorting the rest out). I just need to know one small thing:
I got two entries in GRUB of Ubuntu after I upgraded. I don't know if I can delete one. Here's what /boot/grub/menu.lst has:

```
splashimage=(hd0,8)/boot/grub/splash.xpm.gz

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=328b2ee3-b946-4b0a-b536-1e2839be45cb ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=328b2ee3-b946-4b0a-b536-1e2839be45cb ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=328b2ee3-b946-4b0a-b536-1e2839be45cb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=328b2ee3-b946-4b0a-b536-1e2839be45cb ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

```Which two should I delete? There should be only 3 entries, there are 5.

Thanks in advance,

Umang

---

### Post by didac on 2008-05-07
The entries marked kernel 2.6.22-14-generic correspond to Gutsy Gibbon. The entries marked kernel 2.6.24-16-generic correspond to Hardy Heron.

Check /boot to see if you still have vmlinuz-2.6.22-14-generic and then go to /lib/modules to see if there is still a folder called 2.6.22-14-generic. If so, you still have the old kernel. 

Then it's up to you to delete the entries marked 2.6.22 or keep then, in which case you can boot with two different kernels. I would stick to 2.6.24, which is newer, but leave 2.6.22 until everything works fine.

---

### Post by Umang on 2008-05-07
Thanks!

Yes, I have both vmlinuz-2.6.22-14-generic and vmlinuz-2.6.24-16-generic files.

Does that mean that 7.10 is still installed on my computer?

OK. So I won't change it till everything is fixed. 

Thanks again!

Umang

---

### Post by didac on 2008-05-07
No, you don't have 7.10 anymore. Ubuntu sits on top of the linux kernel. You can have different kernels and the same 8.04 without your noticing much difference.

Later on, Linux may release a new kernel, say 2.6.95 and you bake your new kernel without touching Ubuntu. It may happen, for instance, that you buy a new piece of hardware not supported by 2.6.24 and either you upgrade your whole linux distribution or you bake a new kernel which supports your new hardware.

Glad to help:)

---

### Post by Umang on 2008-05-07
Ah, I think I've understood what you are saying.

Thanks for helping!

Umang

---

