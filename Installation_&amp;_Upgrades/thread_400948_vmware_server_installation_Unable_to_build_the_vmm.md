---
title: "vmware server installation: Unable to build the vmmon module."
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by lopean on 2007-04-04
I was trying to install the vmware server on my laptop when i came across this error:


Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /usr/src/linux-headers-2.6.20-13-generic/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-13-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-13-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


*note i tried changingr the header location from the default after a quick search through the ubuntu forums. Others suggested install g++ header files but im a newb and not to sure how to do that. I think i already have gcc installed on my computer. 

Can someone please help me?? :confused:

Sorry for the double post...

---

### Post by bapoumba on 2007-04-04
> **lopean said:**
> 
Sorry for the double post...
No problem. As it was an exact duplicate in the same sub-forum, i just deleted it. hope this is OK with you.

---

### Post by lopean on 2007-04-04
Thank you. I was trying to figure out how to do that. So does anyone know how to fix my vmware server installation?

---

### Post by lopean on 2007-04-04
ok well after a little more research i figured out how to fix it. Someone suggesting downloading vmware-any-any-update108.tar.gz and everything went smoothly after the install from there.

---

### Post by anders on 2007-05-22
This worked for me as well. The file lopean refers to can be found here:

[http://knihovny.cvut.cz/ftp/pub/vmware/](http://knihovny.cvut.cz/ftp/pub/vmware/)

Just download the file vmware-any-any-updateNNN.tar.gz where NNN is the version number (currently 110). Just run the script and it will patch your vmware files and then you can run vmware-config.pl again.

---

