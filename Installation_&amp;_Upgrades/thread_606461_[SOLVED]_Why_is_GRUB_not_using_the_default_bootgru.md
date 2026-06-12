---
title: "[SOLVED] Why is GRUB not using the default /boot/grub/menu.lst file?"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by davidkahn on 2007-11-08
I just upgraded to Gutsy and noticed that the kernel is still Feisty:

    uname -r
    2.6.20-16-generic

It turns out that while the entries for the Gutsy kernel are in /boot/grub/menu.lst.   For example:

    title           Ubuntu 7.10, kernel 2.6.22-14-generic
    root            (hd0,0)
    kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro quiet splash
    initrd          /boot/initrd.img-2.6.22-14-generic

That they are not showing up in GRUB menu.  On another Gutsy computer that is correctly using the default menu.lst, I can make edits to it and see them affect GRUB.  However,  edits to /boot/grub/menu.lst has no effect on the problem PC.

How do I fix this?  Run grub-install?  Or is the a configuration file somewhere?

I have found some threads that seem related, but no definitive solution.

Thanks.

David

---

### Post by yabbadabbadont on 2007-11-08
Try running "sudo update-grub" and see if your menu.lst file changes.  It might be having a problem with the word, "kernel", in the description.  You might try removing that word.

---

### Post by davidkahn on 2007-11-08
I got brave and did:

sudo grub-install hd0

followed by

sudo update-grub

and GRUB now seems to be using the using /boot/grub/menu.lst

However, now it fails to boot correctly on the Gutsy kernel.  I'm going to try reinstalling the kernel, and will let you know if that works.

Thanks for the quick response.

---

### Post by davidkahn on 2007-11-08
I have now reinstalled linux-image-2.6.22-14-generic and am still having the "File not found" error.

I guess I'll have to learn more about installing the kernel -- another Linux adventure. 8^)

---

### Post by yabbadabbadont on 2007-11-08
Try changing:```
title Ubuntu 7.10, kernel 2.6.22-14-generic
``` To:```
title=Ubuntu 7.10, kernel-2.6.22-14-generic
```
Note the dash that I added between "kernel" and "2.6.22-14-generic".

---

### Post by davidkahn on 2007-11-08
The ultimate solution to this was to download and run Super GRUB  ([http://sgd.howto-linux.de/](http://sgd.howto-linux.de/)).  Super GRUB showed that the Gutsy kernel was on hd1 rather than hd0. So changing "root (hd0,0)" to "root (hd1,0)" allowed /boot/vmlinuz-2.6.20-16-generic to boot.

The only thing left to understand is how it is possible that the new kernel is on a different disk, as the two hard drives in this PC are in a Linux software RAID array (versus having a hardware RAID controller), and one would therefore expect that their contents would be identical.

---

