---
title: "Grub menu.lst missing in jaunty update... help paste the list for /boot/vmlinuz-2.6.2"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by acho on 2009-12-25
My Jaunty 9.04 can't update the grub list. Anybody who had update to /boot/vmlinuz-2.6.28-17-generic...

please paste it for me... I was do in command like this:

> sudo update-grub

nothing change on my grub menu.lst file. I want to edit it manualy. thx for your help.

> sudo gedit /boot/grub/menu.lst

Still like this nothing change:
> title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		0451b92b-66cb-440b-ae78-ef24201d9c21
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0451b92b-66cb-440b-ae78-ef24201d9c21 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		0451b92b-66cb-440b-ae78-ef24201d9c21
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0451b92b-66cb-440b-ae78-ef24201d9c21 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, memtest86+
uuid		0451b92b-66cb-440b-ae78-ef24201d9c21
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows Jablay XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by acho on 2009-12-25
it's done...

just change the number from 16 to 17..... :lolflag:

---

