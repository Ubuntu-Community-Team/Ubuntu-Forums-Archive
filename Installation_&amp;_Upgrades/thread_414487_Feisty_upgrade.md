---
title: "Feisty upgrade"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by sefs on 2007-04-19
After upgrading to feisty it atuo replaced the kernal with the generic one.

So all kinds of things have stopped working 

wireless, vmware, parallels ect...

I am unable to recompile ndiwsrapper or vmware ect because i am getting some kind of compile error now that I was not getting before on edgy.

What do i need to do to get things going again.

I also use a static ip with my cards will network manager the new applet mess this up.

thanks.

---

### Post by sefs on 2007-04-20
this is an example of the comiple erros i am now getting on feisty.  Does any one know how to repair this?

Thanks.

```

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /usr/src/linux-headers-2.6.20-15-386/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

