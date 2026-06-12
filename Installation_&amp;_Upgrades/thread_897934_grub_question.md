---
title: "grub question"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by BlackLLama on 2008-08-22
i have installed arch linux, how do i add its partition to grub bootloaders,
my first partition is vista, 2nd is ubuntu.

---

### Post by Patb on 2008-08-22
You could try reinstalling Grub using [Catlett's How to restore Grub from a Live Ubuntu CD]("http://ubuntuforums.org/showthread.php?t=224351"). 

Cheers, Pat.

---

### Post by BlackLLama on 2008-08-22
i dont need to re install, i just forget how to open the grub menu.lst, and i just need to add arch into it, which i know how to do but i dont know what to write in

---

### Post by Patb on 2008-08-22
Sorry, I misunderstood.
```
sudo gedit  /boot/grub/menu.lst
```
The format will follow what I have here for a debian OS on my system:
```
title           Debian GNU/Linux, kernel 2.6.18-6-686, /dev/hda6
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.18-6-686 root=/dev/hda6 ro quiet 
initrd          /boot/initrd.img-2.6.18-6-686
```
The title can be what you like. 

Note that the partition numbers start at 0 for Grub and 1 for the linux device notation. So here "(hd0,5)" = "/dev/hda6".  So find out where your Arch is and edit the "hd0,5" and "/dev/hda6" accordingly.  

Make sure the file names vmlinuz... and initrd... and paths are correct for your system. 

Hope this helps. 

Cheers, Pat.

---

