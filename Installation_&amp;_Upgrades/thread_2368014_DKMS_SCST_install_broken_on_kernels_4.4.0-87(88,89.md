---
title: "DKMS SCST install broken on kernels 4.4.0-87(88,89)-generic: too many arguments to fu"
date: 2017-08-05
forum: Installation &amp; Upgrades
---

### Post by gstanden on 2017-08-05
I have a general solution for building DKMS-enabled SCST modules that is fully described here: [https://sites.google.com/site/nandydandyoracle/scst/scst-debian-dkms-package-build-from-source-ubuntu-17-04](https://sites.google.com/site/nandydandyoracle/scst/scst-debian-dkms-package-build-from-source-ubuntu-17-04) and the scripts archive is at my github [https://github.com/gstanden/orabuntu-lxc](https://github.com/gstanden/orabuntu-lxc) but Ubuntu 16.04 support is problematic because of some problems apparently in the 4.4.0-x-generic kernel series. There seems to be some issue building DKMS modules confirmed in kernels 4.4.0-87-generic, 4.4.0-88-generic and 4.4.0-89-generic so as a workaround the scripting prompts the user to upgrade to the 16.04.3 LTS HWE kernel (4.10.0-30-generic) which plays nice with DKMS.  Here is the error stack when attempting to install SCST DKMS-enabled *.deb package (built from SCST source code - latest) - and I don't get this problem on any other Ubuntu kernels - Ubuntu 15.04 has no issues and 17.04 has no issues (and even 14.04 has no issues) but on 16.04 for those kernels there is some DKMS problem.

I can stick with the workaround of users installing the 16.04.3 HWE kernel, but I'd like to be able to include a fix for the kernels that are giving this issue (4.4.0-87,88,89-generic kernels).  Anybody know if there is a fix for this?  

There was something on launchpad about this but I didn't really see how to extract a practical step-by-step workaround/fix from the info there: [https://bugs.launchpad.net/ubuntu/+source/iscsitarget/+bug/1701697](https://bugs.launchpad.net/ubuntu/+source/iscsitarget/+bug/1701697)


Thanks, Gil

make[1]: Entering directory '/usr/src/linux-headers-4.4.0-89-generic'
  LD      /var/lib/dkms/scst/3.3.0/build/iscsi-scst/conftest/use_pre_440_wr_structure/built-in.o
  CC [M]  /var/lib/dkms/scst/3.3.0/build/iscsi-scst/conftest/use_pre_440_wr_structure/use_pre_440_wr_structure.o
scripts/Makefile.build:264: recipe for target '/var/lib/dkms/scst/3.3.0/build/iscsi-scst/conftest/use_pre_440_wr_structure/use_pre_440_wr_structure.o' failed
Makefile:1420: recipe for target '_module_/var/lib/dkms/scst/3.3.0/build/iscsi-scst/conftest/use_pre_440_wr_structure' failed
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-89-generic'
echo "" >"conftest/use_pre_440_wr_structure/result-4.4.0-89-generic.txt"
make -C /lib/modules/4.4.0-89-generic/build SCST_INC_DIR=/var/lib/dkms/scst/3.3.0/build/iscsi-scst/../scst/include SUBDIRS=/var/lib/dkms/scst/3.3.0/build/iscsi-scst/kernel modules
make[2]: Entering directory '/usr/src/linux-headers-4.4.0-89-generic'
  CC [M]  /var/lib/dkms/scst/3.3.0/build/iscsi-scst/kernel/iscsi.o
  CC [M]  /var/lib/dkms/scst/3.3.0/build/iscsi-scst/kernel/nthread.o
/var/lib/dkms/scst/3.3.0/build/iscsi-scst/kernel/nthread.c: In function &#8216;do_recv&#8217;:
/var/lib/dkms/scst/3.3.0/build/iscsi-scst/kernel/nthread.c:730:8: error: too many arguments to function &#8216;sock_recvmsg&#8217;
  res = sock_recvmsg(conn->sock, msg,
        ^
In file included from /var/lib/dkms/scst/3.3.0/build/iscsi-scst/kernel/iscsi.h:22:0,
                 from /var/lib/dkms/scst/3.3.0/build/iscsi-scst/kernel/nthread.c:29:
include/linux/net.h:220:5: note: declared here
 int sock_recvmsg(struct socket *sock, struct msghdr *msg, int flags);
     ^
scripts/Makefile.build:258: recipe for target '/var/lib/dkms/scst/3.3.0/build/iscsi-scst/kernel/nthread.o' failed
make[3]: *** [/var/lib/dkms/scst/3.3.0/build/iscsi-scst/kernel/nthread.o] Error 1
Makefile:1420: recipe for target '_module_/var/lib/dkms/scst/3.3.0/build/iscsi-scst/kernel' failed
make[2]: *** [_module_/var/lib/dkms/scst/3.3.0/build/iscsi-scst/kernel] Error 2
make[2]: Leaving directory '/usr/src/linux-headers-4.4.0-89-generic'
Makefile:135: recipe for target 'mods' failed
make[1]: *** [mods] Error 2
make[1]: Leaving directory '/var/lib/dkms/scst/3.3.0/build/iscsi-scst'
Makefile:6: recipe for target 'all' failed
make: *** [all] Error 2

---

