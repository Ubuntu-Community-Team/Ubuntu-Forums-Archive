---
title: "Ubuntu trouble with IBM Aptiva"
date: 2004-12-10
forum: Installation &amp; Upgrades
---

### Post by crayak on 2004-12-10
I installed Ubuntu on my laptop, and it was no trouble at all. So I thought it would be a good idea to install it on my other PC as well. 

The installation goes well, without any errors at all, then I am asked to remove the disk and reboot. It does, but the booting just stops, and there is no reaction at all. Grub has a line of commandoes it runs:

```
root(hd0,0)
     Filesystem type is ext2fs, partitiontype 0x83
kernel /boot/wmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro BOOT_DEBUG=1 quiet splash
     [Linux-bzImage, setup=0x1400, size=0x10ad89]
initrd /boot/initrd.img-2.6.8.1-3-386
     [Linux-initrd @ 0x12bdb000,  0x405000 bytes]
savedefault
boot
```

And thats it. There is no reaction after this. I have tried different install parameters, but no luck. I have also tried to install with LILO-bootloader, but it hangs too. 

The computer is a IBM Aptiva:
PIII 500MHz(512KB), 320MB RAM, 8GB HDD IDE, PCI/ISA Minitwr(3X5), Riva 6X DVD 56K
(IBM Aptiva Type: 2164, Model: 66G)

I hope you can help me out here.  [-o<

---

