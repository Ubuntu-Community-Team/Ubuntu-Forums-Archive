---
title: "Setting Ubuntu 10.04 to Console version"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by jptalledo on 2011-07-15
Hi All

I am trying to setup my Ubuntu 10.04 install in console mode. I will not need the X Windows interface.

I modified /etc/default/grub line to:

GRUB_CMDLINE_LINUX_DEFAULT="text acpi=off"

But I am running a C++ program during the start up using a script stored in /etc/rcS.d/

But when I press an arrow key. The Ubuntu 10.04 Image appears and also I can't brake my program using CTRL+C.

Any ideas?


I also add in the blacklist the vga16fb to disable the frame buffer.

---

### Post by Sef on 2011-07-15
The easy way to have Ubuntu boot into console mode is at the login screen is to change what it will boot into. If I remember correctly, it is on the bottom left (or possibly, the bottom right.) Once you do that at boot, it will ask you if you want this change one time only or permanent.

---

### Post by jptalledo on 2011-07-15
Ubuntu is booting automatically using the default kernel option. I don't have any graphical interface now.

Any other suggestions?

Thanks

---

