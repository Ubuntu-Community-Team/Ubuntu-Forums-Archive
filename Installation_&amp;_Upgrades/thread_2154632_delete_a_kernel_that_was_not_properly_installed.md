---
title: "delete a kernel that was not properly installed"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by fr33c0untry on 2013-06-15
hi all
i tried to compile  kernel-3.9.0 by following the instructions on this link:

[http://www.thegeekstuff.com/2013/06/compile-linux-kernel/](http://www.thegeekstuff.com/2013/06/compile-linux-kernel/)

i switched to root and extracted the files to /usr/src folder .i ran the make command but after a while it logged out by itself.
so i logged in again and assuming that the make process was over and entered the command 'make modules' which was the next instruction.

but when i got to 'make install' it gave an error and requested to enter the 'make' command again.
this time the 'make install ' process ran smoothly.

when i rebooted the screen resolution was smaller and the mouse and keyboard won't respond when i tried to login.

can anyone tell me how to wemove this kernel from the root directory and grub.i haven't done anything with it yet and i'm using the old kernel
thanks

---

### Post by SuperFreak on 2013-06-15
Can you install Ubuntu Tweak from Software centre. It give the option of removing old kernels

---

