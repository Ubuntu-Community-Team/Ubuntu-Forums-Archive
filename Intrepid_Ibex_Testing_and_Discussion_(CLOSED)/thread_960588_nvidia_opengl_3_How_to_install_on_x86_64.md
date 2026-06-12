---
title: "nvidia opengl 3: How to install on x86_64?"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by krausest on 2008-10-27
The new OpenGL 3 beta driver from nvidia is out and I want to try it.
But for reasons I don't understand the kernel has xen support and thus the driver refuses to install.
How do I install the binary nvidia driver?  

stef@hape:~$ uname -a
Linux hape 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux

excerpt from nvidia installer log:
ERROR: The kernel you are installing for is a Xen kernel!
       
       The NVIDIA driver does not currently work on Xen kernels. If 
       you are using a stock distribution kernel, please install 
       a variant of this kernel without Xen support; if this is a 
       custom kernel, please install a standard Linux kernel.  Then 
       try installing the NVIDIA kernel module again.

---

### Post by plun on 2008-10-27
Maybe this patch still works ?

[http://ubuntuforums.org/showthread.php?t=833633](http://ubuntuforums.org/showthread.php?t=833633)

I have a 7600 card and no use for OpenGL3 which is for 8XXX GPUs and above.

Or take a look at nVidias forum.
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

