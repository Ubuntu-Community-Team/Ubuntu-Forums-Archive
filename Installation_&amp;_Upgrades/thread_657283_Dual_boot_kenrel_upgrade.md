---
title: "Dual boot kenrel upgrade"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by mamep on 2008-01-03
Hello,

I have dual boot on my laptop and thinking to give it to my father and get learn him to use ubuntu.

Boot Priority :

- windows
- Ubuntu

But the problem is when there is a kernel upgrade windows entry deleted and replaced with the new installed version of kenel.

So i was thinking if there is a way to keep allways some entries in the menu.lst OR disable kernel upgrade.



thx,

Mamep

---

### Post by ~LoKe on 2008-01-03
> **mamep said:**
> So i was thinking if there is a way to keep allways some entries in the menu.lst OR disable kernel upgrade.

Yes!  Look for the block in your **/boot/grub/menu.lst** that looks like this:
> ## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=79b94531-e9c2-423f-b10e-19d1f6eab496 ro
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

#title          Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
#root           (hd0,1)
#kernel         /boot/vmlinuz-2.6.22-14-generic root=UUID=79b94531-e9c2-423f-b10e-19d1f6eab496 ro single
#initrd         /boot/initrd.img-2.6.22-14-generic

#title          Ubuntu 7.10, memtest86+
#root           (hd0,1)
#kernel         /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
Place the chainloader you use for Windows **UNDER** 
> ### END DEBIAN AUTOMAGIC KERNELS LIST

---

