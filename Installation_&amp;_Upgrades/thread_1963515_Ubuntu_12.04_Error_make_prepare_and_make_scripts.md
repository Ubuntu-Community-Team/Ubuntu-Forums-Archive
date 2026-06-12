---
title: "Ubuntu 12.04 Error make prepare and make scripts"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by Naturofix on 2012-04-22
I'm trying to install a cisco vpn client on a new installation of Ubuntu 12.04

In order to do this I first need to complete the following commands as administrator. 

cd /usr/src/linux and press Enter.
make oldconfig and press Enter.
make prepare and press Enter.
make scripts and press Enter.

I get errors with make prepare and make scripts that prevent me completing the rest of the installation.

cd /usr/src/linux-headers-3.2.0-23-generic/
make oldconfig


scripts/kconfig/conf --oldconfig Kconfig
#
# configuration written to .config
#


make prepare

scripts/kconfig/conf --silentoldconfig Kconfig
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make: *** [prepare0] Error 2

make scripts

  HOSTCC  scripts/selinux/genheaders/genheaders
scripts/selinux/genheaders/genheaders.c:13:22: fatal error: classmap.h: No such file or directory
compilation terminated.
make[3]: *** [scripts/selinux/genheaders/genheaders] Error 1
make[2]: *** [scripts/selinux/genheaders] Error 2
make[1]: *** [scripts/selinux] Error 2
make: *** [scripts] Error 2

any help will be greatly appreciated

---

### Post by gordintoronto on 2012-04-22
Do you understand that Ubuntu 12.04 is beta software?

Have you considered installing vpnc from the software center?

---

