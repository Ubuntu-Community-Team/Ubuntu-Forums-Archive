---
title: "quick question about updates"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by S15_88 on 2008-02-22
When i get a notification about available updates i usually just scan over them to see if they're relevant and if so i install them.  What i honestly just noticed for the first time in almost 1 year of using ubuntu is that some of the updates come up as:
 "(forget what exactly it sasy)....2.6.22-14-generic"

When you restart does it put the latest upgraded version at the top of the grub menu?

lets say i'm using 2.6.22-14-generic and grub looks like this
2.6.22-14-generic
2.6.22-13-generic

if i update to 2.6.22-15-generic will grub now be
2.6.22-15-generic
2.6.22-14-generic 

or

2.6.22-15-generic
2.6.22-13-generic

or

2.6.22-14-generic
2.6.22-15-generic

i'm honestly just royally confused right now i appologize for my stupidity hahaha 

my grub right now is 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a9e6486c-e6b2-4758-bc4f-2c3cf8f1bc63 ro
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a9e6486c-e6b2-4758-bc4f-2c3cf8f1bc63 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a9e6486c-e6b2-4758-bc4f-2c3cf8f1bc63 ro
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a9e6486c-e6b2-4758-bc4f-2c3cf8f1bc63 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

all numbers aside is 14 the latest or 16?  

i'm puzzled and again i feel like a total idiot asking this haha but if anyone can clear this up it would be greatly appreciated.

Thanks, Alain

---

### Post by Pumalite on 2008-02-22
The latest is 24.8, but is in development.

---

### Post by zvacet on 2008-02-23
Last one you install will be first one on grub.

---

### Post by Pumalite on 2008-02-23
Besides that you can always edit menu.lst as you wish.

---

