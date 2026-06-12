---
title: "Fail to build Ubuntu Kernel for OMAP4?"
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2012-08-24
Hi, all:

My hosting computer: Ubuntu 12.04 32bits.

I'm trying to build Ubuntu kernel for OMAP4, strictly following
[http://omappedia.org/wiki/Ubuntu_kernel_for_OMAP4#armhf_cross-compiler_setup](http://omappedia.org/wiki/Ubuntu_kernel_for_OMAP4#armhf_cross-compiler_setup)

I'm actually trying to do ARMHF Cross-Compilation with the kernel 
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=summary)

code
```
fakeroot debian/rules clean
```
brings me the error:
> /bin/bash: kernel-wedge: command not found

and code
```
do_tools=false skipabi=true skipmodule=true dpkg-buildpackage -B -aarmhf -uc -us
```
brings me the error:
> tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: error: tail of debian/changelog gave error exit status 1


Any suggestions please?

Cheers
Pei

---

### Post by jiapei100 on 2012-08-25
Ok, stupid question...
Just install kernel-wedge...

Cheers
Pei

---

