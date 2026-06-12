---
title: "dh_auto_clean: failed to write to debian/debhelper.log: No such file or directory"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by richard_wu0313 on 2010-11-03
fakeroot debian/rules clean
dh  clean
   dh_testdir
i met error after "debuild -S", did anybody meet the same issue?

dh_auto_clean
make[1]: Entering directory `/root/Desktop/package_driver/linux-2.6.35'
  CLEAN   /root/Desktop/package_driver/linux-2.6.35/debian/
make[1]: Leaving directory `/root/Desktop/package_driver/linux-2.6.35'
dh_auto_clean: Compatibility levels before 5 are deprecated.
dh_auto_clean: failed to write to debian/debhelper.log: No such file or directory
END failed--call queue aborted.
make: *** [clean] Error 2
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
debuild: fatal error at line 1340:
dpkg-buildpackage -rfakeroot -D -us -uc failed

---

### Post by richard_wu0313 on 2010-11-08
after further investigation, maybe some error in makefile, but i have no time to debug, so i workaround for this issue. 

when calling "dpkg-buildpackage -rfakeroot"  add other option "-nc" not to clean log file

"dpkg-buildpackage -rfakeroot" will be called when calling "debuild -S"

---

