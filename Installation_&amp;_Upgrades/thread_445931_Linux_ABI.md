---
title: "Linux ABI"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by Hotei on 2007-05-16
Has anyone successfully gotten the Linux A.B.I. ([http://linux-abi.sourceforge.net/](http://linux-abi.sourceforge.net/)) installed on Ubuntu?

I found this page: [http://ace-host.stuart.id.au/russell/files/debian/sarge/kernel-patch-linuxabi/](http://ace-host.stuart.id.au/russell/files/debian/sarge/kernel-patch-linuxabi/) and have been using [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) as a guide. and mashing the two together.

Side note, this is the most complex thing I have attempted with the kernel so please be kind if I have done something blantly stupid.

Here are the steps I have completed:

0. apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
1. download kernel source 2.6.17 /usr/src
2. extract
3. ln -s linux-2.6.17 linux
4. download kernel-patch-linuxabi_20060404.tar.gz to home directory and extract
5. cd /usr/src/linux
6. patch -p1 </home/hotei/abi-sources/kernel-patch-linuxabi-20060404/linuxabi-2.6.17-0.patch
7.  cp /boot/config-`uname -r` ./.config
8. make menuconfig
9. Load alternate config (.config)
10. Go into Executable file formats ->
11. [*] Extened Linux-ABI support (alien binarys and syscalls)
12. <M> SVR3/SVR4 family syscall support for x86 binarys
13. enabled various abi's for the commands I need
14. Exit saving config file
15. make-kpkg clean
16. fakeroot make-kpkg --initrd --append-to-version=-linuxabi-custom-kernel

And this is where things fall apart...

Here is the snipped of the error I get...

Root device is (8, 2)
Boot sector 512 bytes.
Setup is 7063 bytes.
System is 1353 kB
Kernel: arch/i386/boot/bzImage is ready  (#1)
make[1]: Leaving directory `/usr/src/linux-2.6.17'
/usr/bin/make  EXTRAVERSION=-linuxabi-custom-kernel  ARCH=i386 \
                             modules
make[1]: Entering directory `/usr/src/linux-2.6.17'
  CHK     include/linux/version.h
  CC [M]  arch/i386/kernel/msr.o
  CC [M]  arch/i386/kernel/cpuid.o
  CC [M]  arch/i386/kernel/microcode.o
  CC [M]  arch/i386/kernel/apm.o
arch/i386/kernel/apm.c: In function &#8216;suspend&#8217;:
arch/i386/kernel/apm.c:1193: warning: &#8216;pm_send_all&#8217; is deprecated (declared at include/linux/pm_legacy.h:26)
arch/i386/kernel/apm.c:1247: warning: &#8216;pm_send_all&#8217; is deprecated (declared at include/linux/pm_legacy.h:26)
arch/i386/kernel/apm.c: In function &#8216;check_events&#8217;:
arch/i386/kernel/apm.c:1368: warning: &#8216;pm_send_all&#8217; is deprecated (declared at include/linux/pm_legacy.h:26)
arch/i386/kernel/apm.c: In function &#8216;apm&#8217;:
arch/i386/kernel/apm.c:1285: warning: &#8216;event&#8217; may be used uninitialized in this function
  CC [M]  arch/i386/kernel/lcall7.o
  CC [M]  arch/i386/kernel/scx200.o
  CC [M]  arch/i386/kernel/cpu/cpufreq/powernow-k6.o
  CC [M]  arch/i386/kernel/cpu/cpufreq/powernow-k7.o
  CC [M]  arch/i386/kernel/cpu/cpufreq/powernow-k8.o
  CC [M]  arch/i386/kernel/cpu/cpufreq/longrun.o
  CC [M]  arch/i386/kernel/cpu/cpufreq/gx-suspmod.o
  CC [M]  arch/i386/kernel/cpu/cpufreq/speedstep-ich.o
  CC [M]  arch/i386/kernel/cpu/cpufreq/speedstep-centrino.o
  CC [M]  arch/i386/kernel/cpu/cpufreq/speedstep-lib.o
  CC [M]  arch/i386/kernel/cpu/cpufreq/speedstep-smi.o
  CC [M]  arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.o
  CC [M]  arch/i386/kernel/cpu/cpufreq/p4-clockmod.o
  CC [M]  arch/i386/kernel/cpu/cpufreq/cpufreq-nforce2.o
  AS [M]  arch/i386/crypto/aes-i586-asm.o
  CC [M]  arch/i386/crypto/aes.o
  LD [M]  arch/i386/crypto/aes-i586.o
  CC [M]  kernel/intermodule.o
kernel/intermodule.c:178: warning: &#8216;inter_module_register&#8217; is deprecated (declared at kernel/intermodule.c:38)
kernel/intermodule.c:178: warning: &#8216;inter_module_register&#8217; is deprecated (declared at kernel/intermodule.c:38)
kernel/intermodule.c:179: warning: &#8216;inter_module_unregister&#8217; is deprecated (declared at kernel/intermodule.c:78)
kernel/intermodule.c:179: warning: &#8216;inter_module_unregister&#8217; is deprecated (declared at kernel/intermodule.c:78)
kernel/intermodule.c:181: warning: &#8216;inter_module_put&#8217; is deprecated (declared at kernel/intermodule.c:159)
kernel/intermodule.c:181: warning: &#8216;inter_module_put&#8217; is deprecated (declared at kernel/intermodule.c:159)
  CC [M]  fs/binfmt_aout.o
  CC [M]  fs/binfmt_coff.o
fs/binfmt_coff.c: In function &#8216;coff_load_object&#8217;:
fs/binfmt_coff.c:569: warning: implicit declaration of function &#8216;__set_mm_counter&#8217;
fs/binfmt_coff.c:569: error: &#8216;file_rss&#8217; undeclared (first use in this function)
fs/binfmt_coff.c:569: error: (Each undeclared identifier is reported only once
fs/binfmt_coff.c:569: error: for each function it appears in.)
make[2]: *** [fs/binfmt_coff.o] Error 1
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17'
make: *** [stamp-build] Error 2

Thanks for any help.

---

### Post by Hotei on 2007-05-17
Well, I think I found a work around.  I will hopefully find out in the next couple of days whether it worked or not.

I downloaded the kernel-sources and applied the patch to that, compiled cleanly, installed the deb packages, modified /etc/modules and rebooted.

Appears to have the correct modules loaded and working.  Have to wait and see what the developer comes back with.

---

