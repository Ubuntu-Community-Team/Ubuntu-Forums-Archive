---
title: "Mini 110 Wifi Problem - Lucid 10.04"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by simarr24 on 2010-06-10
Just make my first kernel 2.6.34. But now I don't have wifi. I try to reinstall bcmwl-kernel-source like always, but it does not work. It gives me this error.


Error! Bad return status for module build on kernel: 2.6.34 (i686)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

Here is what is in the make.log

DKMS make.log for bcmwl-5.60.48.36+bdcom for kernel 2.6.34 (i686)
Thu Jun 10 06:10:31 CDT 2010
make: Entering directory `/usr/src/linux-2.6.34'
  LD      /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.o
In file included from /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.c:19:
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/include/linuxver.h:23:28: error: linux/autoconf.h: No such file or directory
make[1]: *** [/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-2.6.34'


Please help this newbie :D Thanks.

---

### Post by simarr24 on 2010-06-10
Can anybody please help? I am really stuck on this one. Any lead would be helpful too.

---

