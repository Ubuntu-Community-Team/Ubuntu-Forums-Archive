---
title: "Help with new install"
date: 2005-02-14
forum: Installation &amp; Upgrades
---

### Post by Ronbo on 2005-02-14
I just assembled a new system, Asus K8N motherboard, AMD 64 3000, 512 MB memory, 120 Gig Maxtor HDD, and Geforce 4 video.  Ubuntu goes through the install copies all of the packages, but when it reboots the first time to continue the install it freezes.  When the system reboots I get the message

 'Grub loading stage 1.5' 

'Grub loading,  please wait...'

And it just hangs there.  Can't figure it out, I'm kinda new to linux.  A friend of mine had Ubuntu installed and I liked it alot.  Now I would like to set it up on my box.  I've tried installing it several times but keep getting having the same problem.  Any help would be appreciated.

---

### Post by Ronbo on 2005-02-14
Could it be something I need to disable in the motherboard bios.  I remember there was something I had to disable on a previous Asus motherboard when I installed Libranet, any help would be greatly appreciated.

---

### Post by Ronbo on 2005-02-14
Here is my Grub file, can someone please tell me if this is correct.  Only one hard drive in my system along with a cd-rw

title           Ubuntu, kernel 2.6.8.1-3-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title           Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title           Memory test
root            (hd0,0)
kernel          /boot/memtest86+.bin


Does this look right?

---

