---
title: "Installing Acronis true image on FF"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by Underpants on 2007-04-26
Trying to install true image server for linux version 3883 onto ubuntu 7.04.

OK. In previous versions of Ubuntu, all I needed to run was the following to make the Acronis installer happy:

```

sudo apt-get install rpm build-essential linux-source linux-headers-`uname -r`

```

The installer bombs on installing the kernel module. I think it's because the default install of Ubuntu 7.04 uses this kernel:

```

aaron@aaron-desktop:~/Desktop$ uname -r
2.6.20-15-generic

```

the -generic might be throwing things off. Installing "linux-source" just installs a package named "linux-source-2.6.20" so the installer probably can't find the proper source files.

I don't know. I've attached the appropriate log files. 

Please advise.


Files and original post here:
[http://www.wilderssecurity.com/showthread.php?t=172935](http://www.wilderssecurity.com/showthread.php?t=172935)

---

### Post by Underpants on 2007-04-26
```


DKMS make.log for snapapi26-0.7.16 for kernel 2.6.20-15-generic (i686)
Thu Apr 26 18:31:32 EDT 2007
make: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
find: /linux: No such file or directory
  CC [M]  /var/lib/dkms/snapapi26/0.7.16/build/snapapi26.o
/var/lib/dkms/snapapi26/0.7.16/build/snapapi26.c:205: warning: ‘kmem_cache_t’ is deprecated
/var/lib/dkms/snapapi26/0.7.16/build/snapapi26.c: In function ‘sa_cache_emlist_init’:
/var/lib/dkms/snapapi26/0.7.16/build/snapapi26.c:785: error: ‘SLAB_KERNEL’ undeclared (first use in this function)
/var/lib/dkms/snapapi26/0.7.16/build/snapapi26.c:785: error: (Each undeclared identifier is reported only once
/var/lib/dkms/snapapi26/0.7.16/build/snapapi26.c:785: error: for each function it appears in.)
/var/lib/dkms/snapapi26/0.7.16/build/snapapi26.c: In function ‘sa_cache_emget’:
/var/lib/dkms/snapapi26/0.7.16/build/snapapi26.c:819: error: ‘SLAB_ATOMIC’ undeclared (first use in this function)
make[1]: *** [/var/lib/dkms/snapapi26/0.7.16/build/snapapi26.o] Error 1
make: *** [_module_/var/lib/dkms/snapapi26/0.7.16/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'


```

---

### Post by Underpants on 2007-04-26
```

Detected mdk10: 0x0000

Detected mdk10: 0x0000

Detected mdk: 0x0000

Detected mdk: 0x0000

Detected deb: 0x0000

Detected deb: 0x0000

Detected suse91: 0x0000

Detected suse92: 0x0000

Detected suse93: 0x0000

Detected fc4: 0x0000

Detected fc5: 0x0000

Detected virtuozzo: 0x0000

Detected virtuozzo: 0x0000

Running 'rpm -U --percent --force --nodeps /tmp/RPMS.p77zhG/dkms-2.0.4-2.noarch.rpm':
finished
Running 'rpm -U --percent --force --nodeps /tmp/RPMS.p77zhG/snapapi26_modules-0.7.16-1.noarch.rpm':
finished
Running 'rpm -e trueimage':
error: package trueimage is not installed
finished
Running 'rpm -U --percent --force --nodeps /tmp/RPMS.p77zhG/TrueImageClient-9.1.3883-1.i386.rpm':
/var/tmp/rpm-tmp.11035: 8: chkconfig: not found
finished
Launching '/usr/sbin/dkms install -m snapapi26 -v 0.7.16 2>&1'.

Error! DKMS tree does not contain: snapapi26-0.7.16
Build cannot continue without the proper tree.

Launching '/usr/sbin/dkms ldtarball --force --archive /usr/lib/Acronis/kernel_modules/snapapi26-0.7.16-all.tar.gz 2>&1'.

Warning!  This tarball was created with dkms < 2.0 and contains
no arch info. DKMS will assume the arch: i686

Loading tarball for module: snapapi26 / version: 0.7.16

Loading /usr/src/snapapi26-0.7.16...
Creating /var/lib/dkms/snapapi26/0.7.16/source symlink...

DKMS: ldtarball Completed.

Launching '/usr/sbin/dkms install -m snapapi26 -v 0.7.16 2>&1'.

Error! Could not locate snapapi26.ko for module snapapi26 in the DKMS tree.
You must run a dkms build for kernel 2.6.20-15-generic (i686) first.


Preparing kernel 2.6.20-15-generic for module build:
(This is not compiling a kernel, only just preparing kernel symbols)
Storing current .config to be restored when complete
using presented .config
make oldconfig.....
make prepare-all.....

Building module:
cleaning build area....
make KERNELRELEASE=2.6.20-15-generic -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/var/lib/dkms/snapapi26/0.7.16/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.20-15-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/snapapi26/0.7.16/build/ for more information.
exited with status 10.
Acronis True Image Server Setup failed to build kernel modules. Consult /var/log/trueimage-setup.log and /var/lib/dkms/snapapi26/0.7.16/build/make.log for error messages.
Detected mdk10: 0x0000

Detected mdk10: 0x0000

Detected mdk: 0x0000

Detected mdk: 0x0000

Detected deb: 0x0000

Detected deb: 0x0000

Detected suse91: 0x0000

Detected suse92: 0x0000

Detected suse93: 0x0000

Detected fc4: 0x0000

Detected fc5: 0x0000

Detected virtuozzo: 0x0000

Detected virtuozzo: 0x0000

Running 'rpm -U --percent --force --nodeps /tmp/RPMS.2NJ9Av/dkms-2.0.4-2.noarch.rpm':
finished
Running 'rpm -U --percent --force --nodeps /tmp/RPMS.2NJ9Av/snapapi26_modules-0.7.16-1.noarch.rpm':
finished
Running 'rpm -U --percent --force --nodeps /tmp/RPMS.2NJ9Av/MediaBuilder-9.1.3883-1.i386.rpm':
finished
Running 'rpm -e trueimage':
error: package trueimage is not installed
finished
Running 'rpm -U --percent --force --nodeps /tmp/RPMS.2NJ9Av/TrueImageClient-9.1.3883-1.i386.rpm':
/var/tmp/rpm-tmp.25681: 8: chkconfig: not found
finished
Launching '/usr/sbin/dkms install -m snapapi26 -v 0.7.16 2>&1'.

Error! Could not locate snapapi26.ko for module snapapi26 in the DKMS tree.
You must run a dkms build for kernel 2.6.20-15-generic (i686) first.


Preparing kernel 2.6.20-15-generic for module build:
(This is not compiling a kernel, only just preparing kernel symbols)
Storing current .config to be restored when complete
using presented .config
make oldconfig....
make prepare-all....

Building module:
cleaning build area....
make KERNELRELEASE=2.6.20-15-generic -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/var/lib/dkms/snapapi26/0.7.16/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.20-15-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/snapapi26/0.7.16/build/ for more information.
exited with status 10.
Acronis True Image Server Setup failed to build kernel modules. Consult /var/log/trueimage-setup.log and /var/lib/dkms/snapapi26/0.7.16/build/make.log for error messages.
Detected mdk10: 0x0000

Detected mdk10: 0x0000

Detected mdk: 0x0000

Detected mdk: 0x0000

Detected deb: 0x0000

Detected deb: 0x0000

Detected suse91: 0x0000

Detected suse92: 0x0000

Detected suse93: 0x0000

Detected fc4: 0x0000

Detected fc5: 0x0000

Detected virtuozzo: 0x0000

Detected virtuozzo: 0x0000

Running 'rpm -U --percent --force --nodeps /tmp/RPMS.pSJa3F/dkms-2.0.4-2.noarch.rpm':
finished
Running 'rpm -U --percent --force --nodeps /tmp/RPMS.pSJa3F/snapapi26_modules-0.7.16-1.noarch.rpm':
finished
Running 'rpm -U --percent --force --nodeps /tmp/RPMS.pSJa3F/MediaBuilder-9.1.3883-1.i386.rpm':
finished
Running 'rpm -e trueimage':
error: package trueimage is not installed
finished
Running 'rpm -U --percent --force --nodeps /tmp/RPMS.pSJa3F/TrueImageClient-9.1.3883-1.i386.rpm':
/var/tmp/rpm-tmp.10451: 8: chkconfig: not found
finished
Launching '/usr/sbin/dkms install -m snapapi26 -v 0.7.16 2>&1'.

Error! Could not locate snapapi26.ko for module snapapi26 in the DKMS tree.
You must run a dkms build for kernel 2.6.20-15-generic (i686) first.


Preparing kernel 2.6.20-15-generic for module build:
(This is not compiling a kernel, only just preparing kernel symbols)
Storing current .config to be restored when complete
using presented .config
make oldconfig....
make prepare-all....

Building module:
cleaning build area....
make KERNELRELEASE=2.6.20-15-generic -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/var/lib/dkms/snapapi26/0.7.16/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.20-15-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/snapapi26/0.7.16/build/ for more information.
exited with status 10.
Acronis True Image Server Setup failed to build kernel modules. Consult /var/log/trueimage-setup.log and /var/lib/dkms/snapapi26/0.7.16/build/make.log for error messages.
```

---

