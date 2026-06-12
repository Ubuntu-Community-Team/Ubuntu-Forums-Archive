---
title: "How to boot Windows?"
date: 2005-05-20
forum: Installation &amp; Upgrades
---

### Post by BorO on 2005-05-20
Hello!

I have installed Ubunut 5.04 and it runs well but I cant boot into my MS Windows installation.

Ubuntu is installed on my hda2 and Windows on hdb5
This is how it looks in my /boot/grub/menu.lst

[HTML]## ## End Default Options ##

title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
savedefault
boot

title           Windows
root            (hd1,0)
savedefault
chainloader     +1
map             (hd0) (hd1)
map             (hd1) (hd0)

### END DEBIAN AUTOMAGIC KERNELS LIST[/HTML] 

Any ideas? :)

---

### Post by 23meg on 2005-05-20
does windows appear on the boot menu? if so, what error message do you get when you choose it?

---

### Post by BorO on 2005-05-20
> does windows appear on the boot menu? if so, what error message do you get when you choose it? 
Windows appears on the menu and the error I get is following

Filesystem type unknown, partitiontype 0xf

Hope you know what it means :)

---

