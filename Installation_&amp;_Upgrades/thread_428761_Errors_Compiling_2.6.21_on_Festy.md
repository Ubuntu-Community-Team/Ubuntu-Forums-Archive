---
title: "Errors Compiling 2.6.21 on Festy"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by DaveTheAve on 2007-04-30
**Output: **
root@David-Laptop:/usr/src/linux# ls
arch             conf.vars  drivers  init    lib           Makefile.orig  Module.symvers      scripts   stamp-arch-conf       stamp-configure-indep  ubuntu
block            crypto     fs       ipc     linux-2.6.21  Makefile.rej   net                 security  stamp-configure       stamp-debian           usr
config.precious  debian     include  kernel  Makefile      mm             patch-2.6.21.1.bz2  sound     stamp-configure-arch  stamp-indep-conf
root@David-Laptop:/usr/src/linux# make-kpkg clean
exec debian/rules  DEBIAN_REVISION=5:10.Custom  clean

====== making target CLN-common [new prereqs: testdir]======

====== making target CLN-common [new prereqs: ]======
/usr/bin/make -f ./debian/rules real_stamp_clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
====== making target real_stamp_clean [new prereqs: ]======
running clean
test ! -f scripts/package/builddeb.kpkg-dist ||                     \
          mv -f scripts/package/builddeb.kpkg-dist scripts/package/builddeb
test ! -f scripts/package/builddeb.kpkg-dist ||                     \
          mv -f scripts/package/Makefile.kpkg-dist scripts/package/Makefile
test ! -f .config  || cp -pf .config config.precious
test ! -f Makefile || \
            /usr/bin/make    ARCH=x86_64 distclean
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.20-15-generic/drivers/infiniband/hw/amso1100/Makefile: No such file or directory
make[5]: *** No rule to make target `/usr/src/linux-headers-2.6.20-15-generic/drivers/infiniband/hw/amso1100/Makefile'.  Stop.
make[4]: *** [drivers/infiniband/hw/amso1100] Error 2
make[3]: *** [drivers/infiniband] Error 2
make[2]: *** [_clean_drivers] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [real_stamp_clean] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [CLN-common] Error 2
root@David-Laptop:/usr/src/linux#
                                       
[B]
Tutorial Followed:[/B]
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
[B]
Reason for upgrade:
[/B]Toshiba A135-S4467 does not have sound; was told that 2.6.21 fixes this issue.

---

