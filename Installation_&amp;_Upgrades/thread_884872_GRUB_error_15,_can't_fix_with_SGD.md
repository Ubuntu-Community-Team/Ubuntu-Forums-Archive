---
title: "GRUB error 15, can't fix with SGD"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by Ruth E J on 2008-08-09
Hi everyone, I've been trying to install Kubuntu 8.04 with KDE4, but when I reboot after installation I get GRUB error 15. I have tried using Super Grub Disk, and all I get is "SGD has not done it" followed by error 15 or sometimes error 17. I have tried installing 8.04 with KDE3, checked all my disks for defects, and various terminal prompts found from looking up error 15 on here.
Anyone got any ideas?
Thanks

---

### Post by Diabolis on 2008-08-09
[Common_Booting_Errors_and_Some_Possible]("http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible")

from: [grub page]("http://users.bigpond.net.au/hermanzone/p15.htm")

> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

---

### Post by Pumalite on 2008-08-09
Super GRUB can boot your operating system by symlinks to the kernel if you use, from the Main Menu,--> Boot Gnu/Linux and  Other OSes --> Boot Gnu/Linux -->...

Boot with Super GRUB Disk instead, and then with your operating system running you can check your file and correct your menu entry for Linux.
Open your menu.lst file with 'sudo gedit /boot/grub/menu.lst', if you are using Ubuntu Linux.
Use the command 'ls /boot' to check for the correct name for your Linux kernel and initrd.img.
Copy the correct name from the terminal output to the text file and paste it to avoid typos. Don't forget to save the changes in your menu.lst file before your close it.

---

### Post by Ruth E J on 2008-08-10
No, I can't boot from the super grub disk, whichever option I choose from SGD, it says "SGD has NOT done it :(((("
When I boot from the live cd and try to open my menu.lst, I get "command not found."
Am gonna try installing Xubuntu later to see if it makes any difference, is it likely to?

---

