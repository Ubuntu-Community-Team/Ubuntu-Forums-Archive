---
title: "Unable to install NVIDIA 96xx drivers"
date: 2009-05-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrek on 2009-05-24
Hi!

I just upgraded my clean Jaunty install to Karmic and I wanted to get the 3d acceleration to work, but.. "Hardware Drivers" doesn't finish installing the drivers (nvidia-glx-96) - it does not show any errors whatsoever. What's more, I tried to install nvidia-glx-96 manually but it ended up with the following error : ```
Setting up nvidia-96-kernel-source (96.43.10-0ubuntu1) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 96.43.10
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.30-5-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/96.43.10/build/ for more information.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.30-5-generic (i686) first.
Done.

```

I also checked nvidia.com site for their driver package but it won't build as well. Any ideas?

And, uh, /var/lib/dkms/nvidia/96.43.10/build/make.log :
```
DKMS make.log for nvidia-96.43.10 for kernel 2.6.30-5-generic (i686)
Sun May 24 21:59:07 CEST 2009
NVIDIA: calling KBUILD...
make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.30-5-generic/build SUBDIRS=/var/lib/dkms/nvidia/96.43.10/build modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /var/lib/dkms/nvidia/96.43.10/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia/96.43.10/build/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia/96.43.10/build
  cc -Wp,-MD,/var/lib/dkms/nvidia/96.43.10/build/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.0/include  -Iinclude  -I/usr/src/linux-headers-2.6.30-5-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -fno-dwarf2-cfi-asm -I/var/lib/dkms/nvidia/96.43.10/build -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"96.43.10\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /var/lib/dkms/nvidia/96.43.10/build/.tmp_nv.o /var/lib/dkms/nvidia/96.43.10/build/nv.c
In file included from include/linux/bitops.h:17,
                 from include/linux/kernel.h:15,
                 from include/linux/sched.h:52,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/96.43.10/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/96.43.10/build/nv.c:14:
/usr/src/linux-headers-2.6.30-5-generic/arch/x86/include/asm/bitops.h: In function ‘set_bit’:
/usr/src/linux-headers-2.6.30-5-generic/arch/x86/include/asm/bitops.h:64: warning: pointer of type ‘void *’ used in arithmetic
/usr/src/linux-headers-2.6.30-5-generic/arch/x86/include/asm/bitops.h: In function ‘clear_bit’:
/usr/src/linux-headers-2.6.30-5-generic/arch/x86/include/asm/bitops.h:102: warning: pointer of type ‘void *’ used in arithmetic
/usr/src/linux-headers-2.6.30-5-generic/arch/x86/include/asm/bitops.h: In function ‘change_bit’:
/usr/src/linux-headers-2.6.30-5-generic/arch/x86/include/asm/bitops.h:178: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/list.h:6,
                 from include/linux/preempt.h:11,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:54,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/96.43.10/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/96.43.10/build/nv.c:14:
include/linux/prefetch.h: In function ‘prefetch_range’:
include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/96.43.10/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/96.43.10/build/nv.c:14:
include/linux/sched.h: In function ‘object_is_on_stack’:
include/linux/sched.h:2123: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/io.h:22,
                 from include/linux/pci.h:54,
                 from /var/lib/dkms/nvidia/96.43.10/build/nv-linux.h:85,
                 from /var/lib/dkms/nvidia/96.43.10/build/nv.c:14:
/usr/src/linux-headers-2.6.30-5-generic/arch/x86/include/asm/io.h: In function ‘writeq’:
/usr/src/linux-headers-2.6.30-5-generic/arch/x86/include/asm/io.h:70: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/dma-mapping.h:7,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-headers-2.6.30-5-generic/arch/x86/include/asm/pci.h:129,
                 from include/linux/pci.h:1098,
                 from /var/lib/dkms/nvidia/96.43.10/build/nv-linux.h:85,
                 from /var/lib/dkms/nvidia/96.43.10/build/nv.c:14:
include/linux/scatterlist.h: In function ‘sg_virt’:
include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used in arithmetic
In file included from /var/lib/dkms/nvidia/96.43.10/build/nv-linux.h:112,
                 from /var/lib/dkms/nvidia/96.43.10/build/nv.c:14:
include/linux/highmem.h: In function ‘zero_user_segments’:
include/linux/highmem.h:147: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:147: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:147: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:147: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:150: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:150: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:150: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:150: warning: pointer of type ‘void *’ used in arithmetic
/var/lib/dkms/nvidia/96.43.10/build/nv.c: In function ‘nvos_proc_create’:
/var/lib/dkms/nvidia/96.43.10/build/nv.c:502: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/96.43.10/build/nv.c:503: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/96.43.10/build/nv.c:504: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/96.43.10/build/nv.c:524: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/96.43.10/build/nv.c:537: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/96.43.10/build/nv.c:548: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/96.43.10/build/nv.c:558: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/96.43.10/build/nv.c:568: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/96.43.10/build/nv.c:579: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/96.43.10/build/nv.c:586: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/96.43.10/build/nv.c: In function ‘nvos_proc_add_warning_file’:
/var/lib/dkms/nvidia/96.43.10/build/nv.c:613: error: ‘struct proc_dir_entry’ has no member named ‘owner’
make[3]: *** [/var/lib/dkms/nvidia/96.43.10/build/nv.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia/96.43.10/build] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2
```

Thanks in advance.

---

### Post by psyke83 on 2009-05-24
Unfortunately, you will find yourself constantly without a proper NVIDIA driver during the development process. The restricted drivers (especially graphics) are given a very small priority.

NVIDIA usually don't add support for a kernel until it's finalized, and Karmic's kernel is currently based of 2.6.30-rc6 or so.

You can either downgrade to Jaunty, try the "nouveau" driver, or try to patch and manually build the NVIDIA driver (if you can find patches against Ubuntu's kernel version). Even worse for you is that you're using the second-oldest legacy version of the driver, which is given a low priority by NVIDIA.

---

### Post by andrek on 2009-05-24
Thanks. Looks like I'll have to reinstall my Jaunty system, then.

---

### Post by plun on 2009-05-24
If you are skilled maybe this can help you and patch the 96 driver.

[http://www.nvnews.net/vbulletin/showthread.php?t=131597](http://www.nvnews.net/vbulletin/showthread.php?t=131597)


Seems to be the same error as with the 180 driver which now is fixed. 

"[Pavlinux" patch]("http://changelogs.ubuntu.com/changelogs/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-graphics-drivers-180_180.44-0ubuntu2/changelog") is used with Karmics 180.44 driver.

---

### Post by plun on 2009-05-24
Followup, this driver probably works

[http://www.nvnews.net/vbulletin/showthread.php?t=128942](http://www.nvnews.net/vbulletin/showthread.php?t=128942)

```
Added support for X.Org server 1.5 and 1.6.

Improved compatibility with recent Linux 2.6 kernels.
```


EDIT must probably also be patched.....:frown:

--

---

### Post by DanaG on 2009-05-26
Hmm, for me, even on Jaunty, the nvidia 96 driver doesn't work (card is a mobile, integrated GeForce "1 + 1 = 4mx" card) -- for me, it just segfaults the X server in nvidia_drv.so.  That's even with the absolute latest nvidia 96.43.11.  I find it funny -- and pathetic -- that the legacy driver has not actually been major-version upgraded in over a year (if I remember correctly) -- it's been 96.43 this whole time.
In other words, don't hold your breath for nvidia's legacy drivers.

---

### Post by t.rei on 2009-06-08
Hm,

Same Problem. The System (Karmic) runs fine so far, but without a properly working video driver there isn't much testing of the UI possible.

I hope it's a while until I run into more severe incompatibilities with the kernel version I am still running: *kernel 2.6.28-11-generic* - to keep my precious beauty of workflow alive.

---

### Post by tad1073 on 2009-06-08
are those the legacy drivers, if not here is something that might help.

[https://launchpad.net/~thefirstm/+archive/ppa]("http://ubuntuforums.org/showthread.php?t=1163474")

just replace karmic with jaunty and that should give you access to driver 185.18.14, which I am running w/kernel 2.6.30-8

---

### Post by lvlo on 2009-06-09
Found this patch for nVidia 96.43.11 drivers: [http://www.nvnews.net/vbulletin/showthread.php?t=133990](http://www.nvnews.net/vbulletin/showthread.php?t=133990)

---

