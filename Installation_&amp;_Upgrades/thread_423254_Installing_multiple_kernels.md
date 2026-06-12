---
title: "Installing multiple kernels"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by eqspec on 2007-04-25
[FONT="Arial Black"][FONT="Arial"][/FONT][/FONT]Does anyone know how to install multiple kernels and set them up in grub? If so, can someone please help me.
I'm currently running Ubuntu Feisty with the latest kernel image, but my laptop (Toshiba satellite p25-s670) run flawlessly with kernel 2.4.17, and I have no restart issues with this kernel. I am hoping to install that kernel on Feisty if it's possible.
Thanks in advance.

---

### Post by nebousuru on 2007-04-26
> **eqspec said:**
> [FONT="Arial Black"][FONT="Arial"][/FONT][/FONT]Does anyone know how to install multiple kernels and set them up in grub? If so, can someone please help me.
I'm currently running Ubuntu Feisty with the latest kernel image, but my laptop (Toshiba satellite p25-s670) run flawlessly with kernel 2.4.17, and I have no restart issues with this kernel. I am hoping to install that kernel on Feisty if it's possible.
Thanks in advance.


If you can get a .deb package containing the kernel it is usually as easy as installing it.  The grub entry is usually automagic.

If you only have the binary image and module image, you can _**try**_ (i've never done this) copying the files into /boot and creating a new entry into /boot/grub/menu.lst.  If you still have the old install of linux, look at it's menu.lst for the entry and copy that

If you want to recompile a kernel i would look at the [ [COLOR="Blue"]Master Kernel Thread[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel").   This guide will produce a deb package that works automagically, and should be a good enough guideline if you end up needing to recompile an older kernel ( you could do this to get a new package, if you don't have the old one)


As far as compatibility of the 2.4.17 kernel with feisty, i have no idea.  Worth a try, though

---

### Post by eqspec on 2007-04-26
your rightt, it's definetly worth a try. I'll check it out and post my results. Thanks again.

---

