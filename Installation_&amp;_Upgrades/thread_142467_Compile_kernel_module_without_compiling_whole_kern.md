---
title: "Compile kernel module without compiling whole kernel??"
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by luopio on 2006-03-10
Hi

I'd like to compile a new shining xpad-module for the current Dapper-kernel, but I would like to do it without compiling the whole kernel. AFAIK this is possible with the kernel-headers.

I got the xpad.c and xpad.h from CVS at [http://xbox-linux.org](http://xbox-linux.org), but I can't seem to get them compiled correctly. 

What is the correct command to get the module compiled? :confused: 

Thanks for any help!

---

### Post by az on 2006-03-10
That's what the linux-headers are for.

Since you only have two files, it sounds like you are missing some stuff, though.  Is there not a tarball with documentation?

---

### Post by luopio on 2006-03-11
I checked the CVS at [http://cvs.xbox-linux.org/viewcvs.py/xbox-linux/kernel-2.6/drivers/usb/input/](http://cvs.xbox-linux.org/viewcvs.py/xbox-linux/kernel-2.6/drivers/usb/input/) and found only a Makefile and a Kconfig. I checked both out and tried compiling with *make xpad*. This started complaining about not finding linux/slab.h, so I changed the Makefile to include the headers (-I -option) at */usr/src/linux-headers-2.6.15-18/include*. This ended up with a million more errors complaining about the headers themselves.

Do you know what the straight gcc-command would be? I just have one .c-file..

---

### Post by az on 2006-03-11
[QUOTE=luopio]s.

Do you know what the straight gcc-command would be? I just have one .c-file..[/QUOTE]

You need more that that, I think.

---

