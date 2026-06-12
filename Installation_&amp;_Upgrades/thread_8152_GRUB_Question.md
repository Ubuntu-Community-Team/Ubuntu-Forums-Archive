---
title: "GRUB Question"
date: 2004-12-14
forum: Installation &amp; Upgrades
---

### Post by AlexV on 2004-12-14
I just installed Ubuntu along side Fedora Core 3, but skipped installing a bootload since I already have GRUB installed. 
What do I need to change in my 'grub.conf' file to get it to add Ubuntu to by boot menu?

Thanks   :D

---

### Post by Original Brownster on 2004-12-15
[QUOTE=AlexV]I just installed Ubuntu along side Fedora Core 3, but skipped installing a bootload since I already have GRUB installed. 
What do I need to change in my 'grub.conf' file to get it to add Ubuntu to by boot menu?

Thanks   :D[/QUOTE]

Hi,
You'll need to add a stanza to the grub menu, should be in the file
/boot/grub/menu.lst

replacing the (hdx,x) and /dev/hdxx and kernel name with your set-up
from my menu.lst file:

title           Ubuntu, kernel 2.6.8.1-3-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

HTH

---

