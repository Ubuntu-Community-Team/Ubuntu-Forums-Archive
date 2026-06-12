---
title: "How to install any distro with GRUB?"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by Junkbox on 2008-11-12
I was wondering how I can install DSL or puppy from just the .iso with GRUB. I already have GRUB installed and have booted the kernel and initrd from the .iso. When I get to the installer it looks for a CD in the disk drive instead of letting me specify a location for the installation files. Can anyone explain how to do this the right way?

---

### Post by w1av on 2008-11-12
Hi Junkbox.

I am pulling my hair out trying to do the same thing! I can't seem to get the entries in /boot/grub/menu.lst correct. I tried to use the ISO for Feather Linux and DSL but to no avail.....It seemd to uncompress the kernel ok...you can see all the text fly by....but then it stop dead with "cannot find linux filesystem....dropping you to a (limited) shell..."
So it is finding the kernel and starts to boot, but runs into trouble with those other files, initrd.gz and minirt24......I don't know how to enter the right info in the /boot/grub/menu.lst. Menu.lst is the file where you make additional entries for other OS's on your machine. But you have to get the references and locations of the kernel, and the compressed image. Unfortuneatley different distrso call those files by other names and it is confusing on what EXACTLY to look for. I posted a message for heklp similar to yours this morning but no response yet......If I do get some usefull information I will pass it along....bob

---

### Post by Junkbox on 2008-11-12
Yeah, I think both of us are having the same problem here but I haven't tried adding entries into the menu.lst. Instead Iv'e been booting the kernel from the grub command like like this:

root (hd0,0) 
kernel /vmlinuz
initrd /initrd.gz
boot

It seems to boot the kernel just fine but then it says "Cannot find MEPIS filesystem".

---

### Post by louieb on 2008-11-12
Don't know that you can do that with GRUB. However it is possible to boot to an iso file on your hard drive. [HOWTO Boot from any .iso file without needing a working CD-ROM]("http://ubuntuforums.org/showthread.php?t=666267")

---

### Post by Junkbox on 2008-11-12
Hey W1av, 

Have you tried adding something like this to your menu.lst?

title Your Linux installer of choice
kernel (hd0,0)/boot/"linux_kernel_filename"  
initrd (hd0,0)/boot/"ramdisk_filename"

I dont know if you need to add other distro specifics though.

Is it possible for you to boot from a USB device? 
If so, UNetbootin might be able to create a bootable installer for you. [http://lubi.sourceforge.net/unetbootin.html]("http://lubi.sourceforge.net/unetbootin.html")

---

