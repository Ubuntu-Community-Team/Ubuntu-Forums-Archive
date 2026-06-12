---
title: "Kernel Panic after kernel upgrade &amp; Screen freezing under xorg"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by regneva on 2006-09-17
Hi,

I have two problems, couldn't find answers to it on the internet, so am posting here in hope help from the community over here..

1) I upgraded the ubuntu kernel to 2.16.15.24, using the update-manager, after that the system refuses to boot. I get a kernel-panic, this is the full message:
"Kernel panic - not syncing: VFS unable to mount fs on unknown-block (33, 72)"

The previous kernels installed boot just fine. I thought this might be a grub problem and looked at menu.lst to see if there is anything wrong with the default entry, the only difference I saw was that there was no initrd entry for the default entry. I added "initrd.linux" as the initrd for that entry, but that didnt make any difference. Any ideas, pointers?

2) This is a probelm I've been facing since ages (RH8-9, Fedora, Ubuntu breezy and now dapper). I think this is a known bug called "Screen-freezes but pointer moves" bug.

When running xorg, the screen freezes but the pointer keeps moving. This happens generally when the memory usage is full and some app is using an internet connection. If I ssh into the machine and see, Xorg is stuck at 99% CPU usage in some NV_Sync function.

I have GeForce2 MX 400 chipset based card. Is there a known solution to this bug?

Thanks in advance.

---

### Post by beeboob on 2006-09-18
I also have problems whit that kernel..

So i hobe some one can help you

---

### Post by rudiz on 2006-09-18
Try this:

sudo dpkg-reconfigure xserver-xorg

---

### Post by uboltun on 2006-09-18
> **rudiz said:**
> Try this:

sudo dpkg-reconfigure xserver-xorg

Turn off RanderAccell in /etc/X11/xorg.conf
see here [http://www.ubuntuforums.org/showthread.php?t=254648&highlight=geforce2](http://www.ubuntuforums.org/showthread.php?t=254648&highlight=geforce2)

---

