---
title: "VMware Workstation 6.02"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by ghost_ryder35 on 2008-04-02
Last night upgraded to Hardy Heron from Gutsy.  Everything went smooth ;)  Besides that seriously it was good.  I go to open VMware Workstation and it would not open, double click on the icon and nothing does not error out or anything.  Went to open it from the terminal and it said it did not exisist.  So I assumed that the Upgrade anniliated my VMware install so I went to reinstall it however it errors at the following place
```

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-12-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-12-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:83:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:168: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:23,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:84:
/tmp/vmware-config1/vmmon-only/./include/x86cpuid.h:383:1: warning: "BIT_MASK" redefined
In file included from include/linux/kernel.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:11:
include/linux/bitops.h:7:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config1/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:84:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config1/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:84:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:198: warning: initialization from incompatible pointer type
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```
I started googling and found that I should

"Mar 21, 2008 4:18 PM DirkKoopman  says:

fixing it is quite easy.

1. untar /usr/lib/vmware/modules/source/vmmon.tar in somewhere like /tmp
2. edit vmmon-only/include/vcpuset.h

change line 74 from asm/bitops.h to linux/bitops.h

3. tar cvf vmmon.tar vmmon-only
4. mv /usr/lib/vmware/modules/source/vmmon.tar /usr/lib/vmware/modules/source/vmmon.tar.orig
5. cp vmmon.tar /usr/lib/vmware/modules/source

and try vmware-config.pl again."

Tried that and it did not work.  So anyone else have an idea about what I could do to fix this.  Thanks a lot!

---

### Post by ghost_ryder35 on 2008-04-02
OOps, can a MOD move this to the Hardy forums.  Sorries :)

---

### Post by ghost_ryder35 on 2008-04-02
no one?

---

### Post by jshein on 2008-04-03
Try using VMware Workstation 6.0.3
I am currently using this with no issues on 8.04, after making the modification previously mentioned.

[http://www.vmware.com/download/ws/lic_603_lin.html](http://www.vmware.com/download/ws/lic_603_lin.html)

---

### Post by Pres-Gas on 2008-04-03
I can confirm this...totally came in under my radar.

---

### Post by ghost_ryder35 on 2008-04-03
> **Pres-Gas said:**
> I can confirm this...totally came in under my radar.
Thanks for the tips guys.  Instead I downloaded and installed VMware Workstation 6.5 beta which is working pretty good so far, installed without problems.  Only thing I am working on is figuring out why my NAT interface is not operational.  P.S. for the beta you dont need a key and it has some cool new features.  I do not like how they dumbed down the creating a new virtual machine wizard though, but to each his own.  Have a great one.  Should I mark this as solved as we found work arounds but did not solve the problem at hand?

---

