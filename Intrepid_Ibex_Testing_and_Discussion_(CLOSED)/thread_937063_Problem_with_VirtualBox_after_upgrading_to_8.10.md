---
title: "Problem with VirtualBox after upgrading to 8.10"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by CalvinChile on 2008-10-03
Hi, can somebody help me on this:

I upgraded from 8.04 to Kubntu 8.10, but when I tried to start VirtualBox 1.6 it failed so I run the command 
sudo vboxdrv setup 

but it fails and the log file content is

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-4-generic/build SUBDIRS=/tmp/vbox.1 SRCROOT=/tmp/vbox.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-4-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /tmp/vbox.1/.tmp_versions ; rm -f /tmp/vbox.1/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.1
  gcc -Wp,-MD,/tmp/vbox.1/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-4-generic/
arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-de
claration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-un
wind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-
statement -Wno-pointer-sign -I/lib/modules/2.6.27-4-generic/build/include -I/tmp/vbox.1/ -I/tmp/vbox.1/include -I/tmp/vbox.1/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_R
ING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DUSE_NEW_OS_INTERFACE_FOR_MM -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(
SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.1/linux/.tmp_SUPDrv-linux.o /tmp/vbox.1/linux/SUPDrv-linux.c
In file included from /tmp/vbox.1/linux/SUPDrv-linux.c:35:
/tmp/vbox.1/SUPDRV.h:99:30: error: asm/semaphore.h: No such file or directory
/tmp/vbox.1/linux/SUPDrv-linux.c: In function ‘supdrvOSGipResume’:
/tmp/vbox.1/linux/SUPDrv-linux.c:1331: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vbox.1/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-4-generic'
make: *** [vboxdrv] Error 2

Any idea on how should I proceed?

Thanks
Nicolas

---

### Post by howefield on 2008-10-03
Try installing the version of Virtualbox from Synaptic Package Manager, it is version 2.0.2 so will be a bit more advanced than 1.6.

It should prompt you to remove the old modules as part of the install.

---

### Post by CalvinChile on 2008-10-03
Thanks, I will give it a try!

---

### Post by Rocket2DMn on 2008-10-03
Moved to Intrepid Ibex Testing and Discussion
Please remember that Intrepid is still a development release and is subject to more-than-normal breakage.  AFAIK, 8.10 does not work under vbox, and doesn't really play nice in any virtualization software.

---

### Post by CalvinChile on 2008-10-03
After installing Vbox 2.0.2 from the repositories, the machine started fine (WindowsXP guest on Kubuntu 8.10), but lost access to the USB devices.

Any hint on how to correct this?

Thanks,
Nicolas

---

### Post by howefield on 2008-10-03
You could try the command in the first post of this thread.

[http://ubuntuforums.org/showthread.php?t=828927](http://ubuntuforums.org/showthread.php?t=828927)

Works fine for me on Hardy, but I don't know if it will on Intrepid.

---

### Post by inportb on 2008-10-03
> **CalvinChile said:**
> After installing Vbox 2.0.2 from the repositories, the machine started fine (WindowsXP guest on Kubuntu 8.10), but lost access to the USB devices.

Any hint on how to correct this?

You probably wany the proprietary version, not the opensource version. Get the deb from virtualbox.org.

---

### Post by djg5211 on 2008-10-04
inportb is correct.

Open source version of Virtualbox 2+ does NOT have USB support.
I run it here with Kubuntu 8.10 as the host and Windows XP as a guest.

For my cell phone utilities i MUST have XP to run it and i
discovered the USB thing AFTER i had installed the ose VB.

Cheers!
Dave

---

