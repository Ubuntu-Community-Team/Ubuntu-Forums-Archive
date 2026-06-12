---
title: "Installing Linux Kernel on Virtualbox/Bochs"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by Jamie_Edwards on 2012-07-12
Hi guys,

Is it possible to compile and install the Linux kernel onto either Virtualbox or just run it in Bochs?

The only thing is, I want only the kernel, nothing else, reasons being is because I want to develop my own window manager/desktop UI.

Any ideas?

Sorry if this is completely the wrong place for asking this.

Thanks.

Jamie

---

### Post by Cheesemill on 2012-07-13
You need more than just the kernel, you need the GNU tools amongst other things (a bootloader, a shell etc...) to have a usable system.

The easiest thing for you to do would probably be to install a VM using the mini ISO.
This will give you a system with the absolute mininum packages required for a bootable system.
[http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/)

If you don't have a network connection you could also use the alternate install CD to install a minimal CLI system.
[http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)

---

### Post by Jamie_Edwards on 2012-07-14
> **Cheesemill said:**
> You need more than just the kernel, you need the GNU tools amongst other things (a bootloader, a shell etc...) to have a usable system.

The easiest thing for you to do would probably be to install a VM using the mini ISO.
This will give you a system with the absolute mininum packages required for a bootable system.
[http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/)

If you don't have a network connection you could also use the alternate install CD to install a minimal CLI system.
[http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)

Thanks, I'll have a look at the first link

---

