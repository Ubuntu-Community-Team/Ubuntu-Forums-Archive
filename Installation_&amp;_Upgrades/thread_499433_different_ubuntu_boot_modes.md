---
title: "different ubuntu boot modes?"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by oxeimon on 2007-07-12
So I've just installed ubuntu, and when I boot up and GRUB loads, I get 5 choices, the the two interesting ones are as follows(with their script as per /boot/grub/menu.lst

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0262ab28-6f90-4239-8af0-d3388db6b70f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.04 (7.04) (on /dev/sda3)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda3
initrd		/boot/initrd.img-2.6.20-15-generic 
savedefault
boot


So my question is...what's the difference between these two?

---

