---
title: "trouble compiling vmware-tools modules on 2.6.20-16"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by CyDharttha on 2007-06-09
hi all, i'm trying to install vmware-tools in this fiesty vmware image. when running the config.pl, it informs me that it wants to build a module, then asks for kernel-headers location. /usr/src/linux-headers-2.6.20-16-generic exists; uname -r shows this as my currently running kernel. /lib/modules/2.6.20-16-generic also exists. i have tried both, to no avail. it tells me:

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /lib/modules/2.6.20-16-generic/build/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.20-16-generic).  Even if the module were to
compile successfully, it would not load into the running kernel.
```

what is the proper usage here? thanks in advance for any help!

---

### Post by Netsurfer on 2007-06-12
I extracted this answer from another thread.

Beginning from kernel 2.6.18 the version.h was changed by utsrelease.h so you have to rename version.h and [COLOR="Red"]copy utsrealease.h over version.h[/COLOR]

Now you can recompile VMware tools ignoring all errors. 

You can check /etc/X11/xorg.conf to see if all (screen/mouse) is Ok. You probably have to manually copy vmmouse. Check another thread to resolve this issue.

[http://ubuntuforums.org/showthread.php?t=412562&highlight=vmmouse&page=2](http://ubuntuforums.org/showthread.php?t=412562&highlight=vmmouse&page=2)

Bye

---

### Post by CyDharttha on 2007-06-12
thanks very much i'll see how that goes. later!

---

