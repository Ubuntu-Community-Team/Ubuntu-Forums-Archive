---
title: "flippin' GRUB, i hate it."
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by thesanders on 2008-02-12
hey peeps,
having some problems with booting ubuntu 7.10 with kernel 22-14, i get an "Error 17: cannot mount selected partition" when i select it from the startup menu, and when i try loading vista it gives me "Error 12: Invalid device requested" :( 

here's my menu.lst:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f3a51abf-bb6c-49eb-a0bb-069a5960df37 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f3a51abf-bb6c-49eb-a0bb-069a5960df37 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

all help is greatly appreciated =)

---

### Post by Dennis on 2008-02-12
What output does fdisk -l give?

---

### Post by zxscooby on 2008-02-12
Try reading this post [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

also this site is quite helpful [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by DavidTangye on 2008-02-12
Should root        (hd1,0) be (hd0,1)? (Assuming just one hard disk, linux in the second partition)

---

### Post by zxscooby on 2008-02-13
I would have to agree with the previous poster.

---

