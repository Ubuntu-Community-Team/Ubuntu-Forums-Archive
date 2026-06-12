---
title: "Edit menu for multi-boot systems?"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by zx6r1033 on 2008-08-21
Is there any way to edit the startup menu on multi-boot systems? eg: removing unwanted options and renaming certain options.

---

### Post by Pumalite on 2008-08-21
Post:
cat /boot/grub/menu.lst
You can edit with:
gksudo gedit /boot/grub/menu.lst

---

### Post by zx6r1033 on 2008-08-21
Am I correct in assuming that this is the section that I need to edit:





## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0131c1fc-9c91-4f25-9e6e-02c0d6f666bf ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0131c1fc-9c91-4f25-9e6e-02c0d6f666bf ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7648f4b9-66ad-4c37-be38-f3fd05aa93a1 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7648f4b9-66ad-4c37-be38-f3fd05aa93a1 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by zx6r1033 on 2008-08-21
Nevermind... I answered my own question. lol. 


Thank you!

---

