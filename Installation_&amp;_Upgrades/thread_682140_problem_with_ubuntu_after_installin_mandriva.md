---
title: "problem with ubuntu after installin mandriva"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by benniebrown07 on 2008-01-29
I just installed mandriva on my 80 gb hard drive i wanted it to dual boot with Ubuntu but for some reason when i reboot my computer it goes straight to mandriva no menu or anything. Inside mandriva i can find the partition ubuntu is on so I guess its still there. Is there some way mandriva bumped ubuntu of the OS menu or something? Ive read about how xp does that when u install it to dual boot. Could this be the same?

---

### Post by taurus on 2008-01-29
Mandriva installed it own version of GRUB to MBR so you need to edit it and add an entry for Ubuntu.  If you are not sure how to add it, just look at the /boot/grub/menu.lst for Ubuntu on how.

---

### Post by benniebrown07 on 2008-01-29
> **taurus said:**
> If you are not sure how to add it, just look at the /boot/grub/menu.lst for Ubuntu on how.

I'am still not sure how i have to add it when i searched for /boot/grub/menu.lst  a text document popped up.Also Im pretty sure ubuntu is on hda1

Heres what it said:

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/boot/gfxmenu
default 0

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/hda5  resume=/dev/hda7 splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

title linux-nonfb
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/hda5  resume=/dev/hda7
initrd (hd0,4)/boot/initrd.img

title failsafe
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/hda5  failsafe
initrd (hd0,4)/boot/initrd.img

---

