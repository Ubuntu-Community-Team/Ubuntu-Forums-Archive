---
title: "Grub2  - Dos Images files"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by ylafont on 2011-03-03
I copied memdisk from  /usr/lib/syslinux/ over the to my floppy disk image (dos622.img) and booted int the grub command prompt to see if i could load the image manually. with the following

linux /boot/memdisk
initrd /boot/dos622.img 

but nothing occurs, it just goes back the the command prompt. 

When i try

linux16 /boot/memdisk
initrd /boot/dos622.img 

i get  "linux-bz image, setup -0x600, size 0x5apc form the linux16 command and
"You need to load a kernel first" form the Initrd command.

any suggestions?

---

### Post by grahammechanical on 2011-03-03
I really do not know what you are talking about but should you not include a path statement for the file that you wish to run? In other words, you need to tell Grub where the file is. Of course I could be wrong.

Regards.

---

### Post by ylafont on 2011-03-03
Forgive me, I was not clear enough
 
When booting and a DOS image files  with the  the following entry
 
menuentry 'Boot To DOS (version 6.22)' {
linux /boot/burg/memdisk
initrd /boot/burg/bootdisk/dos622.img
}
 
I got no messages or error warnings.  
 
The solution seemed to be to use Linux16 and initrd16. which solved the problem of booting the imagefile.

---

