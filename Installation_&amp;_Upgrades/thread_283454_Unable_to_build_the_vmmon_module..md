---
title: "Unable to build the vmmon module."
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by cypher1 on 2006-10-24
I'm trying to install VMWare workstation 4.5 and i get this error message after running vmware-config.pl

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running 
kernel? [/lib/modules/2.6.17-6-686/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

/bin/sh: Syntax error: "(" unexpected (expecting "then")
Unknown VMware Workstation 4.5.2 build-8848 detected. Building for VMware Workstation 3.2.x
make: Entering directory `/tmp/vmware-config21/vmmon-only'
/bin/sh: Syntax error: "(" unexpected (expecting "then")
make[1]: Entering directory `/tmp/vmware-config21/vmmon-only'
/bin/sh: Syntax error: "(" unexpected (expecting "then")
make[2]: Entering directory `/tmp/vmware-config21/vmmon-only/driver-2.6.17-6-686'
.././linux/driver.c:0: warning: -malign-loops is obsolete, use -falign-loops
.././linux/driver.c:0: warning: -malign-jumps is obsolete, use -falign-jumps
.././linux/driver.c:0: warning: -malign-functions is obsolete, use -falign-functions
In file included from /lib/modules/2.6.17-6-686/build/include/linux/irq.h:21,
                 from /lib/modules/2.6.17-6-686/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.17-6-686/build/include/linux/hardirq.h:6,
                 from /lib/modules/2.6.17-6-686/build/include/linux/interrupt.h:10,
                 from .././linux/driver.c:52:
/lib/modules/2.6.17-6-686/build/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory
make[2]: *** [driver.d] Error 1
make[2]: Leaving directory `/tmp/vmware-config21/vmmon-only/driver-2.6.17-6-686'
make[1]: *** [deps] Error 2
make[1]: Leaving directory `/tmp/vmware-config21/vmmon-only'
make: *** [auto-build] Error 2
make: Leaving directory `/tmp/vmware-config21/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and 
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


I've tried to install the "any-any" patch but it was useless. Hope someone could help

---

### Post by cypher1 on 2006-10-24
I tried to re-install it. Now it gives me this:

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config34/vmmon-only'
make -C /lib/modules/2.6.17-6-686/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-6-686'
  CC [M]  /tmp/vmware-config34/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config34/vmmon-only/linux/driver.h:18,
                 from /tmp/vmware-config34/vmmon-only/linux/driver.c:38:
/tmp/vmware-config34/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config34/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config34/vmmon-only/linux/driver.h:18,
                 from /tmp/vmware-config34/vmmon-only/linux/driver.c:38:
/tmp/vmware-config34/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:62: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config34/vmmon-only/linux/driver.c:131: warning: initialization from incompatible pointer type
/tmp/vmware-config34/vmmon-only/linux/driver.c:135: warning: initialization from incompatible pointer type
make[2]: *** [/tmp/vmware-config34/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config34/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-6-686'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config34/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and 
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by TrAvELAr on 2006-10-24
Install linux-headers and then for this question:

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.17-6-686/build/include] 

try:

/usr/src/linux-2.6.17-10-386/include

Should compile ok for you then.  This is of course assuming that you are running 2.6.17-10.  If not, substitute for your linux version.

---

### Post by cypher1 on 2006-11-02
I got it working after installing g++ headers. Others should try it too

---

### Post by Tomas on 2006-11-09
Which g++ headers? I tried looking for them but no go :(

---

### Post by vmalloc on 2006-11-15
This link helps:
[https://help.ubuntu.com/community/InstallingVMware#head-9973a76766d2a1a45c0da13567ce73c227904cbf](https://help.ubuntu.com/community/InstallingVMware#head-9973a76766d2a1a45c0da13567ce73c227904cbf)

You should notice that some changes are required in the script presented there, like change the $START directory initialized in it.

---

### Post by Tomas on 2006-11-15
Thanks I installed it with a patch that I downloaded but I cannot remember where :P

---

### Post by vmalloc on 2006-11-20
For vmware player users: vmware player 1.0.3 includes a compatible binary distribution of vmmon kernel module for Edgy's default kernel. This makes the above script unnecessary, and the installation runs smoothly.

---

### Post by Jango on 2007-05-20
A LAME SOLUTION that i found in my case:

Go to the VMware website and download the RPM package for linux (instead of tar) and convert it to the debian package using alien. THen install as a debian package. Worked very well for me :D

Good luck!

---

### Post by veloce on 2007-05-21
> **Jango said:**
> A LAME SOLUTION that i found in my case:

Go to the VMware website and download the RPM package for linux (instead of tar) and convert it to the debian package using alien. THen install as a debian package. Worked very well for me :D

Good luck!

Or you can just use the vmware server that's in the fiesty repository!

---

### Post by snowa on 2007-06-07
I get an error when using this directory:



The path "/lib/modules/2.6.20-16-generic/build" is an existing directory, but 
it does not contain a "linux" subdirectory as expected.


Any ideas?




> **TrAvELAr said:**
> Install linux-headers and then for this question:

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.17-6-686/build/include] 

try:

/usr/src/linux-2.6.17-10-386/include

Should compile ok for you then.  This is of course assuming that you are running 2.6.17-10.  If not, substitute for your linux version.

---

### Post by wgtripp on 2007-06-09
I solved this problem by re-installing automatix for 7.04 and the then re-installing vmware-server via Automatix.  I had both running under 6.10 but the 7.04 upgrade uninstalled automatix, and broke vmware.  Automatix installs vmware-server 1.0.3. Lastly, I uninstalled the existing vmware-server install.  Then, I installed the vmware-server-kernel-modules via Synaptic, prior to the Automatix install, but I do not know if that was necessary.

The installation of automatix is available here:
[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.5-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.5-7.04feisty_i386.deb)

Automatix is installed into the System Tools menu.  Run it and browse for Virtualization; and there you will find Vmware Server (and Player too!). Once the install is complete, the Vmware Server Console will be available under the System Tools menu.

Griggz

---

### Post by wgtripp on 2007-06-09
Somehow managed to dupliicate my post... sorry.

---

### Post by SubWolf on 2007-06-10
Also be aware of [this situation](http://www.debuntu.org/how-to-vmware-server-workstation-under-ubuntu-feisty) ([http://www.debuntu.org/how-to-vmware-server-workstation-under-ubuntu-feisty](http://www.debuntu.org/how-to-vmware-server-workstation-under-ubuntu-feisty)), which I'm in the process of fixing.

... and [this one](http://www.deaconsworld.org.uk/2007/01/22/more-vmware-problems-in-fedora/) too (patch almost works)...

... and finally, if you get a file not found error for config.h, do (using the correct modules directory for your kernel version):

cd /lib/modules/2.6.20-16-386/build/include/linux/
ln -s autoconf.h config.h

---

### Post by Tnhl1989 on 2008-05-01
After sudo ./runme.pl i get this

Updating /home/tony/vmware/vmware-config.pl ... already patched
Updating /home/tony/vmware/vmware ... No patch needed/available
Updating /home/tony/vmware/vmnet-bridge ... No patch needed/available
Updating /home/tony/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /home/tony/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/home/tony/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/home/tony/vmware/vmware-config.pl". Do you want this script to invoke the 
command for you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/home/tony/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

VMware 2 or VMware Express detected, building for VMware 2, VMware Express and VMware Workstation 4.0.x.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config3/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config3/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config3/vmmon-only/common/vmx86.h:19,
                 from /tmp/vmware-config3/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config3/vmmon-only/common/cpuid.c:15:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config3/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.
For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".
Execution aborted.

---

### Post by magnus07 on 2008-05-21
I had the same problem.
The solution is described here:
[http://communities.vmware.com/docs/DOC-3850](http://communities.vmware.com/docs/DOC-3850)
and briefly you have to:
*****************************
DirkKoopman  says:

fixing it is quite easy.

1. untar /usr/lib/vmware/modules/source/vmmon.tar in somewhere like /tmp
2. edit vmmon-only/include/vcpuset.h

change line 74 from asm/bitops.h to linux/bitops.h

3. tar cvf vmmon.tar vmmon-only
4. mv /usr/lib/vmware/modules/source/vmmon.tar /usr/lib/vmware/modules/source/vmmon.tar.orig
5. cp vmmon.tar /usr/lib/vmware/modules/source

and try vmware-config.pl again.
******************************************

It works for me too.

---

