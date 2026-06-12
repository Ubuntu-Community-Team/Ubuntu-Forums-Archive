---
title: "VMWare vsock module compilation error"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by purecharger on 2010-10-14
I upgraded to 10.10 this morning and VMWare v7.1.2 (build 301458) failed to compile the necessary modules for it to startup. I found a patch that others have had success with here:

[https://answers.launchpad.net/vmware-ubuntu/+question/128677](https://answers.launchpad.net/vmware-ubuntu/+question/128677)

And I get a compilation error on the vsock module:

```

make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/driverLog.o
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/notify.o
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/stats.o
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/util.o
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/vsockAddr.o
  CC [M]  /tmp/vmware-root/modules/vsock-only/driverLog.o
  LD [M]  /tmp/vmware-root/modules/vsock-only/vsock.o
/tmp/vmware-root/modules/vsock-only/driverLog.o: In function `Panic':
(.text+0x110): multiple definition of `Panic'
/tmp/vmware-root/modules/vsock-only/linux/driverLog.o:(.text+0x110): first defined here
/tmp/vmware-root/modules/vsock-only/driverLog.o: In function `DriverLog_Init':
(.text+0x0): multiple definition of `DriverLog_Init'
/tmp/vmware-root/modules/vsock-only/linux/driverLog.o:(.text+0x0): first defined here
/tmp/vmware-root/modules/vsock-only/driverLog.o: In function `Warning':
(.text+0x1b0): multiple definition of `Warning'
/tmp/vmware-root/modules/vsock-only/linux/driverLog.o:(.text+0x1b0): first defined here
/tmp/vmware-root/modules/vsock-only/driverLog.o: In function `Log':
(.text+0x160): multiple definition of `Log'
/tmp/vmware-root/modules/vsock-only/linux/driverLog.o:(.text+0x160): first defined here
make[2]: *** [/tmp/vmware-root/modules/vsock-only/vsock.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vsock-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [vsock.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vsock-only'

```

Any ideas?

---

### Post by dabl on 2010-10-14
First, install the build-essential package, and the kernel-headers-`uname -r' package.

Then, download the two files from here: [http://communities.vmware.com/thread/272625](http://communities.vmware.com/thread/272625)

Copy them both somewhere like /tmp, and run the one named "patch-modules.sh" -- it will call the other script and run it.

Worked correctly on my 10.10 Kubuntu system.

---

### Post by purecharger on 2010-10-14
Thanks for the reply, but that is the patch I had already applied and got me past the original compile failures. Even with the patch I am failing the compile of vsock.ko, however, I can start VMWare without that since it provides the VMCI sockets which apparently are not required for operation?

---

