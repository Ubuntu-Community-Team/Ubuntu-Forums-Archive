---
title: "Need to remove excess files from /boot to continue upgrade"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by kasrahbar on 2008-05-16
So I am upgrading from Feisty to Gutsy and ultimately to Hardy. But, upon upgrading, I am given an error that there is not enough space on /boot. Having checked multiple threads about this issue, I went and uninstalled some of the older kernels in /boot to free up some space. While I successfully freed up space, I need 2 Mb more free space to continue upgrading. Is there anything else I can safely do to continue upgrading?

So heres all the stuff thats in /boot and their sizes:

total 16989
 401 abi-2.6.20-16-generic               12 lost+found
  75 config-2.6.20-16-generic            94 memtest86+.bin
   1 grub                              1015 System.map-2.6.20-16-generic
6849 initrd.img-2.6.20-16-generic      1693 vmlinuz-2.6.20-16-generic
6849 initrd.img-2.6.20-16-generic.bak

Perhaps I can relocate or delete one of the chunkier files so I can upgrade. In particular, I got my eye on initrd.img-2.6.20-16-generic.bak since it is a backup file, but I don't know what it does and whether it is essential.

Thanks for any of your help.

---

### Post by macaholic on 2008-05-16
You could probably delete the .bak without any dire consequences, as long as your kernel doesn't panic and corrupt itself mid upgrade. Once you get through the first few install of the upgrade, you should have a partially functional kernel to work with even if it did crash, panic, and corrupt, which is a worst case scenario.

---

