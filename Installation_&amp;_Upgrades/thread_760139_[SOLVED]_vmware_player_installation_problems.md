---
title: "[SOLVED] vmware player installation problems"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by absolutezero1287 on 2008-04-19
I installed vmware player by converting for a .rpm to a .deb using alien. I tried clicking on the icon and nothing would happen so I ran the command in the terminal and was told that it had to be correctly configured. So I tried that and the trouble came at this section: "What is the location of the directory of C header files that match your running
kernel?" can anyone help?


root@Mixed-up:~/Desktop# /usr/bin/vmplayer
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

root@Mixed-up:~/Desktop# /usr/bin/vmware-config.pl.
bash: /usr/bin/vmware-config.pl.: No such file or directory
root@Mixed-up:~/Desktop# /usr/bin/vmware-config.pl
Making sure services for VMware Player are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config2/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config2/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config2/vmmon-only/common/vmx86.h:18,
                 from /tmp/vmware-config2/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config2/vmmon-only/common/cpuid.c:14:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config2/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by fazavon on 2008-04-19
you will need to use the any-any method 

[http://www.howtoforge.com/installing-vmware-server-1.0.4-on-ubuntu-7.10](http://www.howtoforge.com/installing-vmware-server-1.0.4-on-ubuntu-7.10)

this works very well... both vmware 1.4 and 1.5 on 7.10 and 8.04 

thanks

//j

---

### Post by absolutezero1287 on 2008-04-19
Thanks, but like I said all that I have to do is configure it via: /usr/bin/vmware-config.pl. I tried the first two commands for the build environment and nothing hapened. Also bear in mind that I'm using vmware 2.03.

---

### Post by fazavon on 2008-04-21
you will have to run the /usr/bin/vmware-uninstall.pl first

then do the walk through

---

### Post by absolutezero1287 on 2008-04-21
Thanks, that worked.

---

### Post by fazavon on 2008-04-21
anytime :)

---

