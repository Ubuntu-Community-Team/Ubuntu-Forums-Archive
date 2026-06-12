---
title: "virtualbox problem with upgrade to 11.04"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by shortmort37 on 2012-01-24
Newbie here.  I upgraded to 11.04, and my virtualbox stopped working.  I was getting some complaint about Samba4, and I did the deinstall recommended here:

[http://ubuntuforums.org/showthread.php?t=1727547](http://ubuntuforums.org/showthread.php?t=1727547)

Still, I'm getting this complaint when I go to start my virtual XP environment:
---
Kernel driver not installed (rc=-1908 )

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv.  Please reinstall the kernel by executing

'/etc/init.d/vboxdrv setup'
---

So, I do that as root, and it fails.  It tells me "Look at /var/log/vbox-install.log to find out what went wrong".  Below, I paste the contents of that log file.  Where to go from here?

Uninstalling modules from DKMS
  removing old DKMS module vboxhost version  3.2.10

------------------------------
Deleting module version: 3.2.10
completely from the DKMS tree.
------------------------------
Done.
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/3.2.10/source ->
                 /usr/src/vboxhost-3.2.10

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.38-13-generic-pae -C /lib/modules/2.6.38-13-generic-pae/build M=/var/lib/dkms/vboxhost/3.2.10/build....(bad exit status: 2)
0
0
Failed to install using DKMS, attempting to install without
Makefile:170: *** Error: /usr/src/linux (version 2.6.38.8 ) does not match the current kernel (version 2.6.38-13-generic-pae).  Stop.

---

### Post by shortmort37 on 2012-01-25
*bump*.

OK, I looked at this thread:

[https://www.virtualbox.org/ticket/9456](https://www.virtualbox.org/ticket/9456)

Here's that part that caught my eye:

> This is how I solved the problem:

apt-get install linux-headers-2.6.39.4
cd /lib/modules/2.6.39.4; ln -s /usr/src/linux-headers-2.6.39.4 build
/etc/init.d/vboxadd setup

I did the apt-get install for linux-headers-2.6.38-13-generic-pae, but I already had the headers.  I cd to

    /lib/modules/2.6.38-13-generic-pae

and executed

    /etc/init.d/vboxdrv setup

Here's what it reported:

> WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: All config files need .conf: /etc/modprobe.d/lirc-blacklist, it will be ignored in a future release.
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Bad return status for module build on kernel: 2.6.38-13-generic-pae (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxhost/3.2.10/build/ for more information.


Here's the make.log:

> DKMS make.log for vboxhost-3.2.10 for kernel 2.6.38-13-generic-pae (i686)
Wed Jan 25 17:58:10 EST 2012
make: Entering directory `/usr/src/linux-headers-2.6.38-13-generic-pae'
  LD      /var/lib/dkms/vboxhost/3.2.10/build/built-in.o
  LD      /var/lib/dkms/vboxhost/3.2.10/build/vboxdrv/built-in.o
  CC [M]  /var/lib/dkms/vboxhost/3.2.10/build/vboxdrv/linux/SUPDrv-linux.o
In file included from /var/lib/dkms/vboxhost/3.2.10/build/vboxdrv/include/VBox/types.h:30:0,
                 from /var/lib/dkms/vboxhost/3.2.10/build/vboxdrv/linux/../SUPDrvInternal.h:35,
                 from /var/lib/dkms/vboxhost/3.2.10/build/vboxdrv/linux/SUPDrv-linux.c:33:
/var/lib/dkms/vboxhost/3.2.10/build/vboxdrv/include/iprt/types.h:97:31: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/var/lib/dkms/vboxhost/3.2.10/build/vboxdrv/linux/SUPDrv-linux.o] Error 1
make[1]: *** [/var/lib/dkms/vboxhost/3.2.10/build/vboxdrv] Error 2
make: *** [_module_/var/lib/dkms/vboxhost/3.2.10/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.38-13-generic-pae'

What next?

adTHANKSvance
Dan

---

### Post by vt_antik on 2012-02-02
I just worked around this by uninstalling VirtualBox 3.2 via
```
apt-get remove virtualbox-3.2
```

and downloading and installing the 11.04 package for VirtualBox 4.1.8 available here
[https://www.virtualbox.org/wiki/Linux_Downloads]("https://www.virtualbox.org/wiki/Linux_Downloads")

---

