---
title: "Kernel Update &amp; VMware"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by gargo2000 on 2007-09-11
I've been at this for hours and hope someone has a solution for me.

I was working on getting a dual monitor setup which it had me download the new kernel (linux-headers-2.6.15-29-686) which in turn killed VMware.  I'm trying to reconfigure VMware and last time I remember the files were in /usr/src/* (* = directory of the current header).  Well, 686 is installed, but in /usr/src/ there is no directory and VMware is asking:

"The directory of kernel headers (version 2.6.15-28-386) does not match your
running kernel (version 2.6.15-29-686).  Even if the module were to compile
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]  "  ... so my question is, where did it install to?

---

