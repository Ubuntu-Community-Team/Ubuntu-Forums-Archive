---
title: "nvidia driver ioctl error"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by lo.j on 2011-05-21
hi all.

i have a minimal ubuntu desktop and i'm trying to install the latest nvidia driver (downloaded from their website) and i got the following error:
> 
/tmp/selfgz2431/NVIDIA-Linux-x86_64-256.53/kernel/nv.c: At top level:
/tmp/selfgz2431/NVIDIA-Linux-x86_64-256.53/kernel/nv.c:426:5: error: unknown field ‘ioctl’ specified in initializer
/tmp/selfgz2431/NVIDIA-Linux-x86_64-256.53/kernel/nv.c:426:5: warning: initialization from incompatible pointer type
make[3]: *** [/tmp/selfgz2431/NVIDIA-Linux-x86_64-256.53/kernel/nv.o] Error 1
make[2]: *** [_module_/tmp/selfgz2431/NVIDIA-Linux-x86_64-256.53/kernel] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2


i had to apt-get even gcc and make, so i'm probably missing some required package...

thanks a lot.

---

### Post by Lekensteyn on 2011-07-29
See [http://www.nvnews.net/vbulletin/showpost.php?p=2303016&postcount=3](http://www.nvnews.net/vbulletin/showpost.php?p=2303016&postcount=3)

---

