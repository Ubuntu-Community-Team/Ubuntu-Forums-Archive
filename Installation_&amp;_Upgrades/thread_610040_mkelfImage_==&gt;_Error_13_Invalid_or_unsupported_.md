---
title: "mkelfImage ==&gt; Error 13: Invalid or unsupported executable format"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by leond on 2007-11-11
I used mkElfImage ver 2.7 to create a single bootable elf image with this syntax

sudo mkelfImage --command-line="ro root=/dev/hd1 quiet splash console=tty0 console=ttyS0,115200n8" --kernel=/boot/vmlinuz-2.6.20-16-generic --initrd=/boot/initrd.img-2.6.20-16-generic --output=/boot/linuxTest_2.6-generic.elf

My menu.lst entry is
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=74414430-11c6-41bd-99b9-03774c3b69ba ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=74414430-11c6-41bd-99b9-03774c3b69ba ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=74414430-11c6-41bd-99b9-03774c3b69ba ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=74414430-11c6-41bd-99b9-03774c3b69ba ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu, Combined Kernel initrd
root		(hd1,0)
kernel		/boot/linuxTest_2.6-generic.elf root=UUID=74414430-11c6-41bd-99b9-03774c3b69ba ro quiet splash


On reboot, from grub menu, I selected 'Ubuntu, Combined Kernel initrd' and it threw this error
Error 13: Invalid or unsupported executable format

Any help will be appreciated.

---

### Post by Pumalite on 2007-11-11
[http://users.bigpond.net.au/hermanzone/p15.htm#13](http://users.bigpond.net.au/hermanzone/p15.htm#13)

---

### Post by leond on 2007-11-11
But it doesn't answer my question.  Was there anything wrong in the menu.lst entry  or any problem with the concatenated image of initrd+kernel ?
Thanks

---

