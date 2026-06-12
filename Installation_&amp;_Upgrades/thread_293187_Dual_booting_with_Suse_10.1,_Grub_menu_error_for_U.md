---
title: "Dual booting with Suse 10.1, Grub menu error for Ubuntu"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by boz on 2006-11-04
Here is my grub option for Ubuntu 6.06:
```

name: Ubuntu, kernel 2.6.15-27-386 (/dev/sda1)###
title 	Ubuntu, kernel 2.6.15-27-386 (/dev/sda1)
root 	(hd0,0)
kernel 	/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash noapic nopcmcia
initrd 	/boot/initrd.img-2.6.15-27-386
savedefault
boot

```
When I try to boot in, it displays a "cannot find file" error and doesn't say what file.  What are some possible causes?

BTW, I'm sure Ubuntu is on hd0,0 and it is sda1.

---

### Post by amohanty on 2006-11-05
try removing this:
**/boot**
from the kernel and initrd lines

AM

---

### Post by boz on 2006-11-05
My problem stems from a misunderstanding of the "savedefault" option.  After reading up on it, I removed that line and it booted up no problem.  I tried your method first, but I wasn't expecting that to work.  I had already checked to make sure that it was the location of the vmlinuz files, but I thought it couldn't hurt to give someone who probably has more experience than me the benefit of the doubt.  I'm sure if you were on my end you would have had it working lickety-split, but it was a good learning experience for me.  Thanks for your help.

---

