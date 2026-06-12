---
title: "make-kpkg help"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by uygr on 2012-01-03
while i was trying to  change kernel of ubuntu 11.04 from 2.6.38.8 to 3.1.6 i made use of make command and found following error messages.
can anyone please help me.
make[4]: *** [silentoldconfig] Error 1
make[3]: *** [silentoldconfig] Error 2
make[2]: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.
make[2]: Leaving directory `/usr/src/linux-3.1.6'
make[1]: *** [debian/stamp/conf/kernel-conf] Error 2
make[1]: Leaving directory `/usr/src/linux-3.1.6'
make: *** [debian/stamp/conf/minimal_debian] Error 2
Failed to create a ./debian directory: Bad file descriptor at /usr/bin/make-kpkg line 984.

---

