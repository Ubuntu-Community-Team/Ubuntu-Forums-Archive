---
title: "Downloading PCI Driver for Ubuntu 20.04 LTS - Fatal error: opening dependency file"
date: 2021-08-25
forum: Installation &amp; Upgrades
---

### Post by marekgal98 on 2021-08-25
Hi,

Downloading a PCI driver for my Ubuntu system.

After cd'ing to the driver source folder (located in Downloads) I ran the 'make' command, output:

rm -f *.mod.c *.o *.ko .*.cmd *.symvers
make -C /lib/modules/5.11.0-25-generic/build/  SUBDIRS=/home/marek/Downloads/Linux_PCI_driver modules
make[1]: Entering directory '/usr/src/linux-headers-5.11.0-25-generic'
  SYNC    include/config/auto.conf.cmd
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:404:1: fatal error: opening dependency file scripts/basic/.fixdep.d: Permission denied
  404 | }
      | ^
compilation terminated.
make[3]: *** [scripts/Makefile.host:95: scripts/basic/fixdep] Error 1
make[2]: *** [Makefile:562: scripts_basic] Error 2
make[1]: *** [Makefile:737: include/config/auto.conf.cmd] Error 2
make[1]: *** [include/config/auto.conf.cmd] Deleting file 'include/generated/autoconf.h'
make[1]: unlink: include/generated/autoconf.h: Permission denied
make[1]: Leaving directory '/usr/src/linux-headers-5.11.0-25-generic'
make: *** [Makefile:37: default] Error 2

Have already given myself permission to the folder and to the dependency files mentioned in the error

Also from another post tried using 'sudo make clean' as a last resort and was unsuccessful.

---

### Post by ActionParsnip on 2021-08-25
Do you not have to run
```

configure

```
first?

Where did you download the driver from please?

---

### Post by not-published on 2021-08-25
The answer is simple but I won't tell you:  if you have no idea why that happened then CERTAINLY you shouldn't be self-compiling and installing a PCI "replacement of your PCI subsystem" in Ubuntu.

Back up your PC before you continue to a point where you are sure you can recover from a total loss:  because it may will hose your Ubuntu installation badly.  And there won't be anyone to give you 100 hr of lessons if you hose the system.

Your system has PCI drivers already.

To continue you MINIMALLY must stay:  your complete PC setup, your complete UBUNTU version, and exactly where you found this PCI download (it's purpose, MFG, and URL reference).

No one will tell you to install "a different PCI module" without knowing it won't damage the existing PCI is my guess.

---

