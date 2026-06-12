---
title: "Vmware - Unable to build the vmmon module"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by orengolan on 2007-03-27
when installing Vmware on Ubuntu 6.10 i get this: 

```
What is the location of the "gcc" program on your machine? /usr/bin/gcc-4.1

Using compiler "/usr/bin/gcc-4.1". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.17-11-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.17-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
/usr/src/linux-headers-2.6.17-11-generic/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.17-11-generic/scripts/gcc-version.sh: line 12: gcc: command not found
make[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
make[2]: gcc: Command not found
/tmp/vmware-config1/vmmon-only/Makefile:89: *** Inappropriate build environment: you wanted to use gcc version 4.1.2 while kernel attempts to use gcc version .
/tmp/vmware-config1/vmmon-only/Makefile:91: *** For proper build you'll have to replace gcc with symbolic link to /usr/bin/gcc-4.1.  Stop.
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
**Unable to build the vmmon module.**

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


```

---

### Post by raja on 2007-03-27
Looks like you dont have gcc. ```
sudo apt-get build-essential
``` will install the necessary stuff. Then you have to run the configure script for vmware again.

---

### Post by n8bounds on 2007-03-27
he left out on word, but if you wanna cheat, just put this in your terminal ```
 sudo apt-get install build-essential -y && sudo vmware-config.pl 
```

---

### Post by raja on 2007-03-27
> **n8bounds said:**
> he left out on word

Oops! Good you noticed.

---

### Post by orengolan on 2007-03-27
thanks!
eventually i installed VirtualBox..

---

