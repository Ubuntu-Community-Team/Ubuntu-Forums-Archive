---
title: "looking for /usr/src/linux/version.h"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by MaskedMarauder on 2006-11-06
I'm trying to install an evaluation copy of VMWareDesktop on ubuntu linux.

Installation stalls when it tries to build drivers with the message:

"The path "/usr/src/linux/include" is a kernel header file directory, but it does not contain the file "linux/version.h" as expected.  This can happen if the kernel has never been built, or if you have invoked the "make mrproper" command in your kernel directory.  In any case, you may want to rebuild your kernel."

Where (which package) is that file in?  I've installed the usual kernel headers, but this file seems to be missing.

Is there anyway to get a copy of the file version.h belonging to the installed kernel without having to rebuild the stinking kernel?

And, even when I try to build a kernel, I get:
 "/usr/src/linux-source-2.6.15/arch/i686/Makefile: No such file or directory"

Where'd they go?  Why can't I build a kernel I don't want with the ubuntu kernel source package?

---

### Post by evilghost on 2006-11-06
sudo apt-get install build-essential kernel-headers-`uname -r`

I believe that's what you need.

---

### Post by MaskedMarauder on 2006-11-06
> **evilghost said:**
> sudo apt-get install build-essential kernel-headers-`uname -r`

I believe that's what you need.

I tried that, but it doesn't work.  My kernel is 2.6.15-27-k7, but there are no sources for it.  The basic source package is 2.6.7, so I guess that's what I have to go with for now.  I'm building it now, but I'm not sure even that will work since the version file insists its 2.6.7-ubuntu, which won't match the running kernel and so won't allow the module to load.  I suppose I'll end having to run the 2.6.7 kernel to test VMWare.

What a pain.

---

### Post by evilghost on 2006-11-06
sudo apt-get install linux-headers-`uname -r`

Try that...

---

### Post by MaskedMarauder on 2006-11-06
> **evilghost said:**
> sudo apt-get install linux-headers-`uname -r`

Try that...

Nope.  The package is useless for my purposes.  

E.g., the arch directory is just a link to itself:

     arch -> ../linux-headers-2.6.15-27/arch

And none of the header packages include Makefiles.  There are no make files... you just can't build a new module with the headers alone.  Not that I can see.

---

### Post by evilghost on 2006-11-06
> **MaskedMarauder said:**
> Nope.  The package is useless for my purposes.  

E.g., the arch directory is just a link to itself:

     arch -> ../linux-headers-2.6.15-27/arch

And none of the header packages include Makefiles.  There are no make files... you just can't build a new module with the headers alone.  Not that I can see.

Yeah I think you're right.  I ended up installing the kernel source and untarring/bzip2ing it so I could compile VMWare Server.  I know the nVidia kernel module will compile with just kernel headers but now that I think about it VMWare required the kernel source.

Install the linux-source package and cd to /usr/src then "sudo tar -jxvf *.bz2", point the VMWare install to /usr/src/linux-source-2.6.15 or create a symlink to /usr/src/linux.

---

### Post by MaskedMarauder on 2006-11-06
> **evilghost said:**
> Yeah I think you're right.  I ended up installing the kernel source and untarring/bzip2ing it so I could compile VMWare Server.  I know the nVidia kernel module will compile with just kernel headers but now that I think about it VMWare required the kernel source.

Install the linux-source package and cd to /usr/src then "sudo tar -jxvf *.bz2", point the VMWare install to /usr/src/linux-source-2.6.15 or create a symlink to /usr/src/linux.

Bummer.

That won't work either since the version of the module has to match version the running kernel before it'll load.  Since the code is 2.6.7 I have to build a new kernel and run that to test the VMWare.

Is there a way to get a more uptodate patched ubuntu kernel source?  2.6.7  seems a bit antique.

---

