---
title: "kernel compilation error during make modules_install"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by hanish2 on 2013-08-27
cp: cannot stat `/usr/src/linux-source-2.6.34/modules.builtin': No such file or directory
make: *** [_modinst_] Error 1

I get this error when i do **make modules_install **....(after make -j 8)
I checked and my modules-init-tools package are up to date.
i am using VMware workstation on which i am using fedora and on which I am compiling kernel 2.6 for practice purposes and writing device drivers.
I know that modprobe uses this list (modules.builtin) to check for modules built inside the kernel....so I cant just make any .txt file for error to go.
Any help or suggestions welcome.

---

