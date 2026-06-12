---
title: "framebuffer vesa modes not working?"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wizard10000 on 2008-10-12
Upgraded two machines to Intrepid yesterday.  One of them used a vesa framebuffer mode (vga=773, 1024x768x256) in /boot/grub/menu.lst and the machine refused to boot.  Recovery mode option without framebuffer mode booted fine.  Removing 'vga=773' from default boot entry solved the problem.

I searched launchpad and didn't find anything that nailed it exactly so I bugged it.  Bug number is 282105.

---

### Post by MacUntu on 2008-10-12
Vesafb has been replaced with uvesafb, so it's not a bug. AFAIK there is no other way to make it work other than hacking around like described here:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/246269)

---

### Post by wizard10000 on 2008-10-12
> **MacUntu said:**
> Vesafb has been replaced with uvesafb, so it's not a bug. AFAIK there is no other way to make it work other than hacking around like described here:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/246269)

Now that's an ugly workaround  :)

Thanks - gonna go mark my bug as notabug.

---

### Post by iponeverything on 2008-10-12
> **MacUntu said:**
> Vesafb has been replaced with uvesafb, so it's not a bug. AFAIK there is no other way to make it work other than hacking around like described here:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/246269)

I have been mucking around with this problem on and off for week now.. I spend a lot of time in my consoles and rely on them quite a bit to get my system out of the mud - and doing this with the little square in the middle of my lcd just didn't cut it...

thanks that workaround in launchpad works great.

---

### Post by wizard10000 on 2008-10-12
> **iponeverything said:**
> ...thanks that workaround in launchpad works great.

Worked for me too.

---

