---
title: "Grub on floppy, no configuration files seen"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by pjeeanah on 2006-06-13
I chose to install grub on floppy during the installation. When I boot from the floppy, it shows the boot menu correctly and everything boots fine. 

However, it seems that there is nothing on the floppy, no configuration files etc.

I tried to change menu.lst on /boot/grub on the hard disk. When I boot from the floppy, it takes the configuration changes. But again seems that the floppy does not contain any files.

Anyone please could explain. Thanks a lot.

---

### Post by ajgreeny on 2006-06-27
Sorry, I've only just found this thread.  I had the same question when I did this some time ago, before I was confident enough to put grub onto the MBR.

I think the answer is simply that the grub files on the floppy are completely hidden to the OS, both linux and windows, as they both show an empty floppy.

This seems to be a result of Ubuntu not putting boot as a separate partition as many other distro's do.  As an example, when I was testing mepis recently, boot is a separate partition and if you ask to put grub on a floppy, you get everything on the floppy that in Ubuntu is in the /boot folder, including the menu.lst and grub.config files, etc etc.  In Ubuntu grub on the floppy is just pointing to the files in /boot/grub where the system then finds the menu.lst, and displays it.  Quite why no OS's can see anything on the grub floppy I don't know, but I've given up worrying about it now as everything works OK.

---

