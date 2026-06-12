---
title: "IRQPOLL - Booting Xbuntu"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by opiegray on 2007-02-28
When I try to boot my freshly installed 6.10 Edgy Eft, on my older acer travel mate laptop. I seem to get an irq request from irq15, and it recommends I boot with IRQPOLL. So my question is, how exactly do I do this? Or is there another way around it.

Currently my grub is
root  (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet
initrd /boot/initrd.img....
quiet
savedefault
boot

I try and add IRQPOLL to the end of line 2, but when I boot, or escape to menu and go back to the same option it is reset to the same default.. I tried deleteing savedefault and leaving it.

Should I command line and manually edit the GRUB file using sudo?

Or is there something else I can do?

---

### Post by PSAtech on 2007-02-28
Does this happen when you run in under recovery mode?

---

### Post by opiegray on 2007-02-28
Yeah it does.

---

