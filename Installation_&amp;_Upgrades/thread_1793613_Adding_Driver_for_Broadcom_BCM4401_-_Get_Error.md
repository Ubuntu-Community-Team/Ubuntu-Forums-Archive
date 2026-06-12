---
title: "Adding Driver for Broadcom BCM4401 - Get Error"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by clbaines on 2011-06-29
I bought a new router a Linksys/Cisco E2000. Well I have a wireless problem on one of my laptops. The one that was recently upgraded to 11.04. I am trying to get it running. After looking at numerous posts I decided to download and install the correct driver from Broadcom. I have it but I get an error when I try to Make the file.

This is the error message.


clb@clblaptop:~/Desktop/bcm4401/linux/b44-1.00g$ make install
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/clbaines/Desktop/bcm4401/linux/b44-1.00g modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/clbaines/Desktop/bcm4401/linux/b44-1.00g/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/clbaines/Desktop/bcm4401/linux/b44-1.00g] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [default] Error 2

 
I am adept at using vi or gedit and could change the Makefile but I am not sure if I should change all CFLAGS in the Makefile.

Anyone have the solution to this.

---

