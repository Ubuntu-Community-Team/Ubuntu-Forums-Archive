---
title: "Issues installing Vmware"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by ErusGuleilmus on 2008-04-29
Hello, 

I am trying to install VMware Server off on Hardy 64bit. Here is the issue that I am running into: ```
None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:159: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

The installation works perfectly up unto this point. What can I do to remedy this?

Thanks!

---

### Post by malocite on 2008-10-08
*bump*

Same issue on Hardy 32 bit

---

### Post by Raven2k360 on 2008-10-08
I'm not even getting that far -- I'm at the point where it asks for the location of my header files, but when I give it the /usr/src/linux-headers-2.6.24-19/include, it says that the version.h file doesn't exist and that I may need to recompile my kernel.  If I give it the /usr/src/linux-headers-2.6.24-19-generic/include, it tells me that the file version doesn't match the kernel that's running...then it asks me for the path again.  Kinda lost here, anyone have any ideas?  I've still got the terminal window open as of now.

Thanks,

**Edit**  NM, I was pointed in the right direction and got VMware installed without a hitch now.  Running fine, installing WinXPx64 as a test.

---

### Post by heysuz on 2008-10-25
**Edit** NM, I was pointed in the right direction and got VMware installed without a hitch now. Running fine, installing WinXPx64 as a test.
__________________
- Justin 

What was the solution I'm having the same issue?:(:confused:

---

