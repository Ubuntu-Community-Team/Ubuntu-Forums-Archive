---
title: "Install newer nvidia driver for cuda 5?"
date: 2012-06-27
forum: Installation &amp; Upgrades
---

### Post by ryanvade on 2012-06-27
Hello. 

I just recently started working with cuda C++ programming. I want to install the cuda 5 toolkit on my Black Opal (Ubuntu 12.10  x86_64).  I have to install a newer nvidia driver first though. I tried to install the newer driver (302.06.03) and can't install the kernel:

  In file included from /tmp/selfgz12059/NVIDIA-Linux-x86_64-302.06.03/kernel/nv.c:13:0:
   /tmp/selfgz12059/NVIDIA-Linux-x86_64-302.06.03/kernel/nv-linux.h: At top level:
   /tmp/selfgz12059/NVIDIA-Linux-x86_64-302.06.03/kernel/nv-linux.h:114:75: fatal error: asm/system.h: No such file or directory
   compilation terminated.
   make[3]: *** [/tmp/selfgz12059/NVIDIA-Linux-x86_64-302.06.03/kernel/nv.o] Error 1
   make[2]: *** [_module_/tmp/selfgz12059/NVIDIA-Linux-x86_64-302.06.03/kernel] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module 

I have all the linux-headers installed so what am I missing? Any ideas guys?

---

