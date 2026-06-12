---
title: "add Suse into grub"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by foots2015 on 2007-01-12
Before I spend too much time looking. I want to know if somebody could tell me how to add a freshly installed Suse 10.2 into the existing GRUB bootloader. Suse is installed on one of the partitions, I have windows and Ubuntu installed on two others. Suse doesn't show up in GRUB. I can probably enter suse through the console but I don't know how to do it specifically.
I know how to get to ```
gksudo gedit /boot/grub/menu.lst
``` I just need to know what to enter.

any help/pointers are much appreciated.

Tim

---

### Post by Sense on 2007-01-13
I thougth that if you run *dpkg-reconfigure grub*, it's automaticaly generating the right list.

---

### Post by Irony on 2007-01-13
This is quite simple first do;

[PHP]gksudo gedit /boot/grub/menu.lst[/PHP]

Then take your current Ubuntu entry and copy it;

[PHP]# Ubuntu 6.06 /dev/hda6
title		Dapper hda6, 2.6.15-27-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda6 ro quiet splash vga=794
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

# Ubuntu 6.06 /dev/hda6
title		Dapper hda6, 2.6.15-27-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda6 ro quiet splash vga=794
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot[/PHP]

Then replace the second entry with;

[PHP]# Ubuntu 6.06 /dev/hda6
title		Dapper hda6, 2.6.15-27-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda6 ro quiet splash vga=794
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

# Suse 10.2
title		Suse 10.2
root		(hd0,6)
kernel		/boot/vmlinuz-xxxxx root=/dev/hda7 ro quiet splash vga=794
initrd		/boot/initrd.img-xxxxx
savedefault
boot[/PHP]

To find the exact entries navigate your way through nautilus to appropriate /boot file for example in /mnt/suse/boot you will find the kernel and initrd files.

For example my PCLinuxOS installation looks like this;

[PHP]# PCLinuxOS /dev/hda7
title		PCLinuxOS 0.93, hda7
root		(hd0,6)
kernel		/boot/vmlinuz root=/dev/hda7 splash=silent vga=794
initrd		/boot/initrd.img[/PHP]

Here the vmlinuz and initrd.img are actually shortcuts that PCLinuxOS has in the boot file that lead to the actual files so this means the file path is nice and simple.

---

