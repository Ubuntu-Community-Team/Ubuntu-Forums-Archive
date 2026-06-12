---
title: "grub claims &quot;succeeded&quot;, but Vista bootloader still showing up"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by TB2 on 2007-08-25
Hi,

small problem here. I had XP on my PC, and I installed Ubuntu on top of it, with grub as boot loader. Now I installed Vista, and of course grub is gone. What I did next was booting from the Ubuntu CD and type:

sudo grub
>find /boot/grub/stage1               --> gave me "(hd2,0)"
>root (hd2,0)
>setup (hd0)                                 --> gave me found, found, found, succeeded...
>quit

On rebooting, there's the Vista bootloader again. What shall I do? I've got 4 harddrives, sda to sdd, linux/boot is on sdc1.

Why doesn't this work?

---

### Post by confused57 on 2007-08-25
It's possible that grub recognizes the hard drives differently than your bios does, therefore grub's IPL may have been installed to the mbr of one of the other drives...you could try booting first to the other 2 hard drives or you could boot Ubuntu from Vista's bootloader, using easy BCD:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

Grub needs to be installed to the root partition for this to work, i.e. "setup (hd2,0)" from the live cd.

---

### Post by merlinus on 2007-08-25
Look at the boot flags on your partitions.  If it is set for vista, that is why this may be happening.

It needs to be set to ubuntu.

-merlin

---

### Post by TB2 on 2007-08-25
ah-HA! It was the boot flag - didn't think of that.

Thanks!

---

### Post by merlinus on 2007-08-25
Glad it's working!  Easy to overlook the flags.

You might mark this thread as SOLVED for future seekers.

-merlin

---

