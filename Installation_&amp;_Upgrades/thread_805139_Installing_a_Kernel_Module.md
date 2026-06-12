---
title: "Installing a Kernel Module?"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by Skerious on 2008-05-23
Ok i want to try to install the omnibook/toshiba module i downloaded here:

[http://omnibook.sourceforge.net/doku.php](http://omnibook.sourceforge.net/doku.php)


to see if it will fix my battery life/lcd dimming problem on my Toshiba M45


I downloaded the file but have no idea how to install it.  Can someone help me out.  I am a newbie.

commands and all would be appreciated, thanks.

---

### Post by Skerious on 2008-05-26
Any help?  I can't find help for this anywhere.  I am desperate.

---

### Post by dstew on 2008-05-27
Translating [the installation instructions]("http://omnibook.sourceforge.net/doku.php?id=install"), it sounds like you might need to have the full kernel source code in order for the kernel module to compile correctly -- at least that is what he says. Usually, the headers are enough. The full kernel source is pretty huge.

I would try with the headers only first. Find out what your kernel version is using```
uname -r
```Then, use Synaptic and install the linux-kernel-headers package that corresponds to the kernel. I am not sure, but I think you might be able to install just "linux-kernel-headers" and the package management software will get the right one. If the headers are not enough, you will need to get the linux-kernel-source package.

You also need to install the compiler (gcc) and the standard libraries. These are contained in the package **build-essential**.

Once you have installed these, download the source tarball, untar it (double click it), and enter the source directory. From there, do the commands as in the instructions.

---

