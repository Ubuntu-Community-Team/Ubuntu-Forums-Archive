---
title: "T60p hangs with vmlinuz-2.6.24-16-generic"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by fishtoprecords on 2008-04-27
Just installed 8.04 on my Lenovo T60p. Its a dual Core 2 processor. SATA disk.

The 2.6.24 kernel will not boot, it seems to hang trying to find the hard disk to boot from.

the 2.6.22 from Gusty didn't work either.

2.6.20 from Feisty works fine, and seems to work under 8.04

Help, or pointers greatly appreciated.

---

### Post by IT-Joker on 2008-04-27
Hi, 
perhaps your SATA disc problem is the same as I have, see [http://ubuntuforums.org/showthread.php?p=4814927](http://ubuntuforums.org/showthread.php?p=4814927)
Well, but there's no solution yet anyway :( (just wondering if it's the same problem)
But Gutsy worked for me.

---

### Post by MaindotC on 2008-04-27
Yeah when I had this problem i had to go into BIOS and change the hard drive setting to "Compatibility" or something like that.

---

### Post by fishtoprecords on 2008-04-27
> **IT-Joker said:**
> Hi, 
perhaps your SATA disc problem is the same as I have
Sure feels like the same thing.

I had gutsy working for basic stuff, disk, login, etc. but I had display problems and minor stuff like the USB thumb drive support was fubar. So I waited.

I think I'll look at the grub menu stuff, perhaps there are hints there.

thanks

---

### Post by fishtoprecords on 2008-04-28
The grub menu for2.6.24 uses a UUID rather than a path to the root partition. I changed it as below and it seems to work fine.
I do not know what other impact this will have


title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
#kernel         /vmlinuz-2.6.24-16-generic root=UUID=1c33a50d-2b91-4253-83b4-15e47e41c481 ro quiet splash vga=792
kernel          /vmlinuz-2.6.24-16-generic root=/dev/sda3 quiet splash vga=792
initrd          /initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
#kernel         /vmlinuz-2.6.24-16-generic root=UUID=1c33a50d-2b91-4253-83b4-15e47e41c481 ro single
kernel          /vmlinuz-2.6.24-16-generic root=/dev/sda3 single
initrd          /initrd.img-2.6.24-16-generic

---

