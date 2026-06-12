---
title: "VirtualBox Not Working after 8.10 Upgrade"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by ergjoop3 on 2008-11-18
When I try to run my virtual machine, I get


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}


Running sudo /etc/init.d/vboxdrv setup, I get

 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong


/var/log/vbox-install.log has:

Attempting to install using DKMS
info: No menu item ` removing old DKMS module vboxdrv version ' in node `(dir)Top'.

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 1.6.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/1.6.4/source ->
                 /usr/src/vboxdrv-1.6.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-7-generic -C /lib/modules/2.6.27-7-generic/build M=/var/lib/dkms/vboxdrv/1.6.4/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-7-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/1.6.4/build/ for more information.
0
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/lib/modules/2.6.27-7-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_AMD64 -DUSE_NEW_OS_INTERFACE_FOR_MM -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.0/linux/.tmp_SUPDrv-linux.o /tmp/vbox.0/linux/SUPDrv-linux.c
In file included from /tmp/vbox.0/linux/SUPDrv-linux.c:35:
/tmp/vbox.0/SUPDRV.h:104:30: error: asm/semaphore.h: No such file or directory
/tmp/vbox.0/linux/SUPDrv-linux.c: In function ‘supdrvOSGipResume’:
/tmp/vbox.0/linux/SUPDrv-linux.c:1331: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vbox.0/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vboxdrv] Error 2


What is going on here? Thanks in advance.

---

### Post by jflaker on 2008-11-18
do a complete removal, it should leave your data behind....and redownload from repositories......

---

### Post by ergjoop3 on 2008-11-20
Thanks! But I only removed, (not completely) and I had to download the package from the Sun site.

---

