---
title: "Booting Issues with kernel 2.6.27-7"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by juny20 on 2008-11-09
Hello everyone, I am having issues as well with Kubuntu. I upgraded to the new kernel 2.6.27-7 and the laptop is acting up when booting. I don't get the graphical interface to select user. I need to enter the user in terminal and then enter startx to start the session. My grub looks as follows and I notice I have the uui entry:

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7f1cb743-dda2-4956-b0e8-e573d76c532a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7f1cb743-dda2-4956-b0e8-e573d76c532a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7f1cb743-dda2-4956-b0e8-e573d76c532a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7f1cb743-dda2-4956-b0e8-e573d76c532a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7f1cb743-dda2-4956-b0e8-e573d76c532a
kernel		/boot/memtest86+.bin
quiet


Is there anything I should change here?

---

### Post by meierfra. on 2008-11-09
[QUOTE=juny20]I don't get the graphical interface to select user. I need to enter the user in terminal and then enter startx to start the session.[/QUOTE]

Yuor menu.lst looks fine.  So I don't think your problem has anything to do with grub. I suggested to boot into recovery mode and run "xfix".  If that does not cure the problem, start your own new thread.

---

### Post by bapoumba on 2008-11-09
Posts moved to their own thread. Changed the title and added prefix.

---

