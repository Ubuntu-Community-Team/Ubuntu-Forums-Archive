---
title: "Using LABEL with GRUB in menu.lst file"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by DaBruGo on 2006-03-13
Hi folks,

If I use a LABEL command in the menu.lst file, can I leave the root lines out of the menu.lst file?

EXAMPLE:

(before LABEL usage)

title     MY INSTALLATION NAME
root     (hd0,0)
kernel   /boot/vmlinuz-mykernelversionnumber root=/dev/hda1 ...
initrd    /boot/myinitrdfilename ...
boot

(after LABEL usage)

title     MY INSTALLATION NAME
kernel   /boot/vmlinuz-mykernelversionnumber root=LABEL=/mylabelname ...
initrd    /boot/myinitrdfilename ...
boot


I have read somewhere that if you use LABEL (with the e2label command) that the "kernel" line overwrites the initial "root" line during bootup when the menu.lst file is read.

So, If I use LABEL on my partitions do I really need to have the "root" line in my menu.lst file for linux?

My reason for asking is because if I can use LABEL on removable media (USB memory sticks and external drives) and load GRUB to the removable media bootsector, then the LABEL command should always know where to go to bootup Ubuntu - regardless of what PC I connect the removable media into (as long as the device is setup to be the first boot device). 

Any help appreciated,


DAVE

---

### Post by DaBruGo on 2006-03-14
Anybody out there using LABEL in menu.lst?

---

### Post by Ox@NI on 2007-10-03
I just recently installed Ubuntu to replace my reimaging partition for our frameworks. I am also trying to figure out how to add labels in the menu.lst. I just got finished trying to accomplish just that and go a kernel panic. So I know I am not doing it right... I would also appreciate and comments or advice that may help. Thanks!!

---

