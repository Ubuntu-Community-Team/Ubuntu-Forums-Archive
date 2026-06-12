---
title: "bootsplash not working"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by Brando569 on 2005-09-28
i patched my kernel successfully, and followed all of the things on bootsplash.org, but it still doesnt work. i exported (?) the config file to my initial ramdisk and make some changes to my grub menu.lst but all i get is a blank screen when booting to that kernel. heres that section of my menu.lst:

title		Ubuntu, kernel 2.6.10-bootsplash 
root	      (hd0,5)
kernel	    /boot/vmlinuz-2.6.10-bootsplash root=/dev/hda6 ro quiet vga=0x317 splash=silent
initrd	      /boot/initrd.img-2.6.10-bootsplash
savedefault
boot

---

