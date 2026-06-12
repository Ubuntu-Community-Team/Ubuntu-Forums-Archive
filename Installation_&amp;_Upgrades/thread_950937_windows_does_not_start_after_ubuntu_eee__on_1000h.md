---
title: "windows does not start after ubuntu eee  on 1000h"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by Marty Wulferink on 2008-10-17
solution on another thread solved the problem (used teskdisk and rewrote the bootsector)

Hi all, few weeks ago I installed Ubuntu eee on my brand new eee PC 1000h and it runs like, well just like windows did in fact. Everything works as it should and I love it, but...

other family members would like to see their old trusted windows back on the eee PC and although it is still there and appears in the menu of grub, it just won't start. The menu disappears and in the left corner it says "starting ..", but after that nothing happens. 

A short history: During install I resized my first (C) drive and installed Ubuntu eee in the free space that was created in between of C: and D: . On this machine type there is also a partition called EFI (if I recall correctly) which is like a BIOS on "normal" computers, the EFI was, and still is, the last partition. One idea of mine is that maybe windows does not start because D: is "out of order"? I don't think the EFI is the problem, because it should always be the last partition no matter how many partitions are on a disk.

Well, Ubuntu runs, the grub boot menu runs, only windows does not. Anybody know a solution? For a first glance, below is my grub menu.lst file (at least the part that starts the OS). Seems ok to me (compared in to lists I found on the net). Pleas help!
Marty

title           Ubuntu 8.04.1, kernel 2.6.24-21-eeepc
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.24-21-eeepc root=UUID=31fd59fb-be29-4897-978b-2d1c98d12594 ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-eeepc
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-21-eeepc (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.24-21-eeepc root=UUID=31fd59fb-be29-4897-978b-2d1c98d12594 ro single
initrd          /boot/initrd.img-2.6.24-21-eeepc

title           Ubuntu 8.04.1, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by quill3033 on 2008-11-03
How did you go with solving the problem? I've installed ubuntu eee on an 8 gig flash drive and it works great. I'd really like to install it on the hard drive but I'm afraid I won't be able to get to windows, which I need at the moment because I have an e-textbook in there that can't be read by linux. I have also tried mandriva 2009 on the external flash and it's worked great but again, I'm worried that when I install it, it will not give me access to windows. I don't really want to install it from within windows because I did that in my father's desktop (w Hardy) but it doesn't really work as well as normal ubuntu, I find and performance is slower. Anyway, I was wondering how you went and if you had been able to solve the problem.

---

### Post by quill3033 on 2008-11-03
so sorry, just realised you posted a solution. But did you find a way of avoiding the problem in the first place?

---

