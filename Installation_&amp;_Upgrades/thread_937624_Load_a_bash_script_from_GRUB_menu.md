---
title: "Load a bash script from GRUB menu"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by WoPr on 2008-10-04
Hi all!

I would like to know if there is someway to load a bash script from GRUB menu. I need to make a graphical menu to select some options before the session starts, so I want to use the grub menu to perform this.

Thanks in advance :D

Best regards

---

### Post by cariboo on 2008-10-04
You cant add a script to the grub menu, as the os needs to boot up before any scripts can be run. Have a look at this page for more info:

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

jim

---

### Post by WoPr on 2008-10-04
Thanks for your reply, but I have explained it badly.

I need to make a graphical menu and I want to use grub for it.

For example:

title		Linux - script 1
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Linux - script 2
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Linux - script 3
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

So depends on the option the user chooses, it will load a different script when the system boots. The kernel parameters will be the same on all options.

Thanks and best regards

---

### Post by preetamsingh on 2008-10-04
Hi

I am new user to Ubuntu 8


I want to install it on mynew MB ASUS P5N32-E-SLI

Other configrations are

Mother Board    :    ASUS P5N32-E-SLI
PROCESSOR   : CORE 2 DUO E6750 2.66 1333 FSB
Graphic            :    Nvidia 8500 GT 512 MB DDR2
RAM                :    2 GB (2 X 1 GB) KINGSTON DDR2
HARD DISK     :    160 GB 


Please help me


thanks

---

### Post by WoPr on 2008-10-05
Any ideas?

---

