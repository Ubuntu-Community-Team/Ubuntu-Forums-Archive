---
title: "Grub4Dos freezes when loading initrd"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by dc_wmj2 on 2011-05-13
I am using grub4dos 0.44 but can't boot directly into Kubuntu. 
The bootup freezes at the step of reading the initrd.

Can't copy 'n paste the exact bootup-message but it looks similar to this one, I found on another forum-thread:

```
Filesystem type is fat, partition type 0x06
[Linux-bzImage, setup=0x1400, size=0xcff87] 
```Unlike the guy who posted the two lines above, I installed Kubuntu on an ext3-partition (hd0,5), (which is /dev/sda6 in Ubuntu) and without an own bootloader, since I wanna use grub4dos instead of grub2. The installation is fresh - the initrd-file shouldn't be broken.


My menu.lst looks like this:

```
color white/black cyan/black
timeout 5
default (hd0,0)/default

title Kubuntu (Kernel 2.6.35-22)
  fallback 1
  find --set-root uuid () 3940d2a-10c0-4ffd-b845-42f4cffa7045
  root ()/boot
  kernel /boot/vmlinuz-2.6.35-22-generic root=UUID=3940d2a-10c0-4ffd-b845-42f4cffa7045 ro quiet splash    
  initrd    /boot/initrd.img-2.6.35-22-generic
  boot
  savedefault --wait=2
  
  title Windows XP
    fallback 2
    root (hd0,0)
    chainloader (hd0,0)/ntldr
    boot  
    savedefault --wait=2
  
  title Spinrite
  fallback 3
  map  (hd0,0)/spinrite.iso  (hd32)
    map  --hook
    chainloader  (hd32)
    boot
```

---

### Post by dc_wmj2 on 2011-05-14
I tried "Super Grub Disc Hybrid" now. It boots Kubuntu without problem. Any suggestion what to change on my grub4dos-configuration?

---

