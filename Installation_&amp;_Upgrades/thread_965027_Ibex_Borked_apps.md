---
title: "Ibex Borked apps"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Swagman on 2008-10-31
List your apps that have borked since updating to 8:10

Mine.. 

VirtualBox. And Ktorrent (so far)

[i]Vbox borked error.. run sudo /etc/init.d/vboxdrv setup

Still borked.. (Worked last time that broke on 8:04:1)

Gedit.. install log

Attempting to install using DKMS
info: No menu item ` removing old DKMS module vboxdrv version ' in node `(dir)Top'.

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 1.6.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/1.6.2/source ->
/usr/src/vboxdrv-1.6.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel. Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-7-generic -C /lib/modules/2.6.27-7-generic/build M=/var/lib/dkms/vboxdrv/1.6.2/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-7-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/1.6.2/build/ for more information.
0
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/tmp/vbox.1 SRCROOT=/tmp/vbox.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || ( \
echo; \
echo " ERROR: Kernel configuration is invalid."; \
echo " include/linux/autoconf.h or include/config/auto.conf are missing."; \
echo " Run 'make oldconfig && make prepare' on kernel src to fix it."; \
echo; \
/bin/false)
mkdir -p /tmp/vbox.1/.tmp_versions ; rm -f /tmp/vbox.1/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.1
gcc -Wp,-MD,/tmp/vbox.1/linux/.SUPDrv-linux.o.d -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__ -Iinclude -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/lib/modules/2.6.27-7-generic/build/include -I/tmp/vbox.1/ -I/tmp/vbox.1/include -I/tmp/vbox.1/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DUSE_NEW_OS_INTERFACE_FOR_MM -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)" -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.1/linux/.tmp_SUPDrv-linux.o /tmp/vbox.1/linux/SUPDrv-linux.c
In file included from /tmp/vbox.1/linux/SUPDrv-linux.c:35:
/tmp/vbox.1/SUPDRV.h:99:30: error: asm/semaphore.h: No such file or directory
/tmp/vbox.1/linux/SUPDrv-linux.c: In function ‘supdrvOSGipResume’:
/tmp/vbox.1/linux/SUPDrv-linux.c:1331: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vbox.1/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vboxdrv] Error 2
[/i]


And KTorrent

Could not launch menu item
Failed to execute child process "/usr/lib/kde4/bin/ktorrent" (No such file or directory)

This app runs from Alt F2 although there is no longer a built in search facility. And Thats Suxx big time to me. (Yes I went through the prefs etc.. It aint there anymore !!)


Over to you guys....

---

### Post by Sponzenbroekske on 2008-10-31
nothing actually :)

Take the sources of hard for Vbox, works for me :)

```
sudo gedit /etc/apt/sources.list
```

search for the line with virtual box in and change the intrepid to hardy :)

---

### Post by FlappySocks on 2008-10-31
Firefox. Keep crashing.:mad:

---

### Post by Swagman on 2008-10-31
> **Sponzenbroekske said:**
> nothing actually :)

Take the sources of hard for Vbox, works for me :)

```
sudo gedit /etc/apt/sources.list
```

search for the line with virtual box in and change the intrepid to hardy :)

Thanks for the tip but sadly Virtualbox  doesn't appear in any of my sources.lists (I installed it straight from Suns site.)

Not really wanting to do a full re-install of Xvm Virtualbox but it looks highly likely.

:(

---

### Post by kagy on 2008-10-31
Kmymoney - both 0.9.2 in repository and CVS missing dependencies

kmymoney2:
 Depends: libgnutls13 (>=2.0.4-0) but it is not installable
 Depends: libxml++2.6c2a  but it is not installable

---

### Post by Swagman on 2008-10-31
VirtualBox now fixed

Sponzenbroekske pointed me in the right direction..

the repo he mentioned wasn't in my souces.list so... After checking on Suns site..

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free

Updated and now working again


KTorrent running after re-install.

Just gotta suss out how to get Glipper going again.

Anybody notice weird Copy & Paste issues in Firefox now ?

---

