---
title: "VMWare Problem"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by Infinia on 2007-06-11
When I  am installing VMWare server I get this error near the end...

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

Please help me fix this problem!!!

---

### Post by idsfa on 2007-06-11
A quick google provides [[COLOR="Blue"]instructions[/COLOR]]("http://satukubik.com/2007/06/01/installing-vmware-on-ubuntu-704/") on how to fix this.

(google vmmon ‘compat_exit’)

---

### Post by Infinia on 2007-06-11
Thanks... uhh im kind of a noob and I don't under stand the guide... can someone translate this?

# change dir to the installer directory, and enter /lib/modules/source
# untar vmmon.tar

tar xvf vmmon.tar

# edit the file vmmon-only/include/compat_kernel.h, add the following preprocessor statements

/*
 * compat_exit() provides an access to the exit() function. It must
 * be named compat_exit(), as exit() (with different signature) is
 * provided by x86-64, arm and other (but not by i386).
 */
#define __NR_compat_exit __NR_exit
#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,19)
static inline _syscall1(int, compat_exit, int, exit_code);
#endif

# tar back the file

mv vmmon.tar vmmon.orig.tar
tar cvf vmmon.tar vmmon-only

# run vmware-config.pl again

# sudo ./vmware-config.pl

---

### Post by Infinia on 2007-06-11
Anyone?

---

### Post by Infinia on 2007-06-11
Hello? I'm waiting. Please.

---

### Post by drdnl on 2007-06-11
ok, change dir to install directory in the terminal, use the cd command followed by whatever happens to be your install dir. In my case ~/Desktop/vmware-server-distrib/

now type cd /lib/modules/source

tar xvf vmmon.tar

gedit /vmmon-only/include/compat_kernel.h

replace the bit that starts with "/*
* compat_exit() provides an access to the exit() function. It must" with the one in the instructions

mv vmmon.tar vmmon.orig.tar
tar cvf vmmon.tar vmmon-only

and run the ./vmware-config.pl or ./vmware-install.pl

Good luck :)

---

### Post by jgeissin on 2007-06-11
I performed these instructions myself by still get the compile error.  Should the files in /etc/vmware be deleted?
I am running Ubuntu 7.04, I performed the updates it requested post install.
PC is a Dell Precision 530 with a 2Gig Xeon processor and 1 Gig of memory.
VMWare is 5.5 (box version).

---

