---
title: "Too many OS options at load"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by P1ST0LPETE on 2008-05-26
Hi all,

I have installed 2 new versions of Ubuntu since my original install.  Each time I install a newer version, it adds more selections to the GRUB load screen.  My current screen looks like this:

Ubuntu 7.10, kernal 2.6.22-14-generic
Ubuntu 7.10, kernal 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, kernal 2.6.20-16-generic
Ubuntu 7.10, kernal 2.6.20-16-generic (recovery mode)
Ubuntu 7.10, kernal 2.6.20-15-generic
Ubuntu 7.10, kernal 2.6.20-15-generic (recovery mode)
Ubuntu 7.10, memtest86+
Other operating systems:
Microsoft Windows XP Professional

Is there any way that I can clean this up, so that there is only one version of Ubuntu to choose from instead of 3?

---

### Post by iaculallad on 2008-05-26
> **P1ST0LPETE said:**
> Hi all,

I have installed 2 new versions of Ubuntu since my original install.  Each time I install a newer version, it adds more selections to the GRUB load screen.  My current screen looks like this:

Ubuntu 7.10, kernal 2.6.22-14-generic
Ubuntu 7.10, kernal 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, kernal 2.6.20-16-generic
Ubuntu 7.10, kernal 2.6.20-16-generic (recovery mode)
Ubuntu 7.10, kernal 2.6.20-15-generic
Ubuntu 7.10, kernal 2.6.20-15-generic (recovery mode)
Ubuntu 7.10, memtest86+
Other operating systems:
Microsoft Windows XP Professional

Is there any way that I can clean this up, so that there is only one version of Ubuntu to choose from instead of 3?

You can clean it by editing the file named /boot/grub/menu.lst

But be sure to backup it first

Code:

> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

To edit it:

Code:

> sudo gedit /boot/grub/menu.lst

Just be very careful of what you're trying to delete.

---

### Post by grim4593 on 2008-05-27
You could also remove the kernels that you are not using via Synaptic. Usually I keep around two kernel versions "just in case".

---

### Post by schtufbox on 2008-05-27
> **grim4593 said:**
> You could also remove the kernels that you are not using via Synaptic. Usually I keep around two kernel versions "just in case".

yep, that's what I do as well, all I have installed now are:
2.6.24-17-rt

and

2.6.24-16-rt

---

