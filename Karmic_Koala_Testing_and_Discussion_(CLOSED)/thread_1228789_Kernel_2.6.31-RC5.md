---
title: "Kernel 2.6.31-RC5"
date: 2009-08-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by plun on 2009-08-01
Is out...

> Date	Fri, 31 Jul 2009 17:49:42 -0700 (PDT)
From	Linus Torvalds <>
Subject	Linux 2.6.31-rc5


Ok, I've got some pending stuff, but I'm pushing out -rc5 now because it 
does fix a lot of regressions, and some of the pending stuff I'm not 
entirely sure about.

Apart from various regression fixes, the diffstat shows a couple of new 
drivers (at_hdmac, uc2322, gspca/sn9c20x, ds2782 battery driver), and some 
big KMS radeon changes (the Radeon KMS source code may physically be under 
drivers/gpu, but it's only enabled if CONFIG_STAGING is set, and is 
considered unstable).

The diffstat also shows some big power def_config updates and some lguest 
cleanups (much of them whitespace).

Oh, and the USB-3 xhci updates.

Other than that it's mostly pretty small. Shortlog gives a reasonable 
idea..

		Linus

[http://lkml.org/lkml/2009/7/31/266](http://lkml.org/lkml/2009/7/31/266)





Available at Ubuntu Mainline

[http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31-rc5/](http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31-rc5/)

---

### Post by taavikko on 2009-08-01
Yay, got my 3G modem back online
12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

And ath9k seems little more stable (at least for the moment).

modeset isn't still working for my radeon
VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series 1002:95c4
(though haven't looked into this more)

---

### Post by plun on 2009-08-01
> **taavikko said:**
> Yay, got my 3G modem back online
12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem



My Option Globetrotter 3G modem is still broken.

Ubuntus kernel:

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/005397.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/005397.html)

---

### Post by wayne_cat on 2009-08-01
Wow ... Xorg uses 100% CPU with this kernel + the latest xserver-xorg-video-radeon

from Xorg.0.log

```
(EE) open /dev/fb0: No such file or directory
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
```No Problems with 2.6.31-4-generic and the new xserver-xorg-video-radeon.

- Macbook Pro
- ATI x1600
- no errors in .xsession-errors
- no Compiz

*edit: copy&paste error while editing grub ... it only happens _if I enable KMS_*

---

### Post by budluva04 on 2009-08-01
> **wayne_cat said:**
> 
```
(EE) open /dev/fb0: No such file or directory
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
```No Problems with 2.6.31-4-generic and the new xserver-xorg-video-radeon.


1) you can fix that by blacklisting the floppy module
2) no clue, but you should file a bug upstream because there were a boat load of Radeon/KMS fixes in rc5 which this probably has something to do with

sorry not much help, nvidia user here :(

EDIT: haha 1) FB0 doesn't = FD0 i thought you had floppy problems...

framebuffer and radeon problems are out of my league :P my best guess would be disabling KMS and see if you get the errors

not sure how that works for radeon cards, i know the intel cards are i915.modeset=0 in your kernel boot line, for radeon my best guess would be modesetting=0 ???

---

### Post by buzzmandt on 2009-08-01
yay, my ath5k wireless just works again.

---

### Post by taavikko on 2009-08-03
And once again, nvidia module failed to build upon the arrival of the new kernel :)

```
devil@core7:~$ sudo dkms build -m nvidia -v 185.18.14 -k 2.6.31-5-generic

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.31-5-generic module KERNDIR=/lib/modules/2.6.31-5-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/2.6.31-5-generic/build.....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.31-5-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/185.18.14/build/ for more information.
0
0
devil@core7:~$ cat /var/lib/dkms/nvidia/185.18.14/build/dkms.conf 
PACKAGE_NAME="nvidia"
PACKAGE_VERSION="185.18.14"
CLEAN="make clean"
BUILT_MODULE_NAME[0]="nvidia"
MAKE[0]="make module KERNDIR=/lib/modules/$kernelver IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=$kernel_source_dir"
DEST_MODULE_LOCATION[0]="/kernel/drivers/video/nvidia"
AUTOINSTALL="yes"
PATCH_MATCH[0]="^2.6.31"
devil@core7:~$ cat /var/lib/dkms/nvidia/185.18.14/build/make.log 
DKMS make.log for nvidia-185.18.14 for kernel 2.6.31-5-generic (x86_64)
Mon Aug  3 23:13:58 EEST 2009
NVIDIA: calling KBUILD...
make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.31-5-generic/build SUBDIRS=/var/lib/dkms/nvidia/185.18.14/build modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /var/lib/dkms/nvidia/185.18.14/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia/185.18.14/build/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia/185.18.14/build
  cc -Wp,-MD,/var/lib/dkms/nvidia/185.18.14/build/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include  -Iinclude  -I/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/var/lib/dkms/nvidia/185.18.14/build -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /var/lib/dkms/nvidia/185.18.14/build/.tmp_nv.o /var/lib/dkms/nvidia/185.18.14/build/nv.c
In file included from include/linux/bitops.h:17,
                 from include/linux/kernel.h:15,
                 from include/linux/sched.h:52,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv.c:14:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h: In function &#8216;set_bit&#8217;:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h:64: warning: pointer of type &#8216;void *&#8217; used in arithmetic
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h:102: warning: pointer of type &#8216;void *&#8217; used in arithmetic
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h: In function &#8216;change_bit&#8217;:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h:178: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv.c:14:
include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
include/linux/sched.h:2184: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/dma-mapping.h:7,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/pci.h:129,
                 from include/linux/pci.h:1112,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:86,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv.c:14:
include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from /usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/dma-mapping.h:36,
                 from include/linux/dma-mapping.h:107,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/pci.h:129,
                 from include/linux/pci.h:1112,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:86,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv.c:14:
include/asm-generic/dma-mapping-common.h: In function &#8216;dma_map_page&#8217;:
include/asm-generic/dma-mapping-common.h:77: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:113,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv.c:14:
include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
include/linux/highmem.h:149: warning: pointer of type &#8216;void *&#8217; used in arithmetic
include/linux/highmem.h:152: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/compat.h:14,
                 from /usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/mtrr.h:167,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:142,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv.c:14:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/compat.h: In function &#8216;compat_alloc_user_space&#8217;:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/compat.h:210: warning: pointer of type &#8216;void *&#8217; used in arithmetic
  cc -Wp,-MD,/var/lib/dkms/nvidia/185.18.14/build/.nv-vm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include  -Iinclude  -I/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/var/lib/dkms/nvidia/185.18.14/build -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /var/lib/dkms/nvidia/185.18.14/build/.tmp_nv-vm.o /var/lib/dkms/nvidia/185.18.14/build/nv-vm.c
In file included from include/linux/bitops.h:17,
                 from include/linux/kernel.h:15,
                 from include/linux/sched.h:52,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-vm.c:14:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h: In function &#8216;set_bit&#8217;:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h:64: warning: pointer of type &#8216;void *&#8217; used in arithmetic
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h:102: warning: pointer of type &#8216;void *&#8217; used in arithmetic
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h: In function &#8216;change_bit&#8217;:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h:178: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-vm.c:14:
include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
include/linux/sched.h:2184: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/dma-mapping.h:7,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/pci.h:129,
                 from include/linux/pci.h:1112,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:86,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-vm.c:14:
include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from /usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/dma-mapping.h:36,
                 from include/linux/dma-mapping.h:107,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/pci.h:129,
                 from include/linux/pci.h:1112,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:86,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-vm.c:14:
include/asm-generic/dma-mapping-common.h: In function &#8216;dma_map_page&#8217;:
include/asm-generic/dma-mapping-common.h:77: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:113,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-vm.c:14:
include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
include/linux/highmem.h:149: warning: pointer of type &#8216;void *&#8217; used in arithmetic
include/linux/highmem.h:152: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/compat.h:14,
                 from /usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/mtrr.h:167,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:142,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-vm.c:14:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/compat.h: In function &#8216;compat_alloc_user_space&#8217;:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/compat.h:210: warning: pointer of type &#8216;void *&#8217; used in arithmetic
  cc -Wp,-MD,/var/lib/dkms/nvidia/185.18.14/build/.os-agp.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include  -Iinclude  -I/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/var/lib/dkms/nvidia/185.18.14/build -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.14\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /var/lib/dkms/nvidia/185.18.14/build/.tmp_os-agp.o /var/lib/dkms/nvidia/185.18.14/build/os-agp.c
In file included from include/linux/bitops.h:17,
                 from include/linux/kernel.h:15,
                 from include/linux/sched.h:52,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/185.18.14/build/os-agp.c:24:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h: In function &#8216;set_bit&#8217;:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h:64: warning: pointer of type &#8216;void *&#8217; used in arithmetic
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h:102: warning: pointer of type &#8216;void *&#8217; used in arithmetic
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h: In function &#8216;change_bit&#8217;:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/bitops.h:178: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/185.18.14/build/os-agp.c:24:
include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
include/linux/sched.h:2184: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/dma-mapping.h:7,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/pci.h:129,
                 from include/linux/pci.h:1112,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:86,
                 from /var/lib/dkms/nvidia/185.18.14/build/os-agp.c:24:
include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from /usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/dma-mapping.h:36,
                 from include/linux/dma-mapping.h:107,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/pci.h:129,
                 from include/linux/pci.h:1112,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:86,
                 from /var/lib/dkms/nvidia/185.18.14/build/os-agp.c:24:
include/asm-generic/dma-mapping-common.h: In function &#8216;dma_map_page&#8217;:
include/asm-generic/dma-mapping-common.h:77: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:113,
                 from /var/lib/dkms/nvidia/185.18.14/build/os-agp.c:24:
include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
include/linux/highmem.h:149: warning: pointer of type &#8216;void *&#8217; used in arithmetic
include/linux/highmem.h:152: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/compat.h:14,
                 from /usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/mtrr.h:167,
                 from /var/lib/dkms/nvidia/185.18.14/build/nv-linux.h:142,
                 from /var/lib/dkms/nvidia/185.18.14/build/os-agp.c:24:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/compat.h: In function &#8216;compat_alloc_user_space&#8217;:
/usr/src/linux-headers-2.6.31-5-generic/arch/x86/include/asm/compat.h:210: warning: pointer of type &#8216;void *&#8217; used in arithmetic
/var/lib/dkms/nvidia/185.18.14/build/os-agp.c: In function &#8216;KernLoadAGPPages&#8217;:
/var/lib/dkms/nvidia/185.18.14/build/os-agp.c:296: error: &#8216;agp_memory&#8217; has no member named &#8216;memory&#8217;
make[3]: *** [/var/lib/dkms/nvidia/185.18.14/build/os-agp.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia/185.18.14/build] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2
```

---

### Post by sylvester_0 on 2009-08-03
My nVidia module compiled properly. I was only having problems when using the leaked 190 from a PPA.

```
 * Running DKMS auto installation service for kernel 2.6.31-5-generic           
 *  nvidia (185.18.14)... nvidia (185.18.14): Already installed on this kernel.
                                                                         [ OK ]
 *  vboxdrv (3.0.2)... vboxdrv (3.0.2): Already installed on this kernel.
                                                                         [ OK ]
 *  vboxnetadp (3.0.2)... vboxnetadp (3.0.2): Already installed on this kernel.
                                                                         [ OK ]
 *  vboxnetflt (3.0.2)... vboxnetflt (3.0.2): Already installed on this kernel.
                                                                         [ OK ]

```

:D

---

### Post by sylvester_0 on 2009-08-03
Hmm, I just booted into it and X/GDM dies within 2-10 seconds of running. Sometimes I can log in and use it for a sec other times i don't even have enough time to finish typing my password.

Here is my video card:

```
nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
```

I don't see anything out of the ordinary in Xorg.0.log so I'm not sure how to debug this. For now I'm just using .4 - I'm sure it'll get fixed soon :)

---

### Post by paul_in_london on 2009-08-03
nvidia 190.18.03 +  2.6.31-RC5 is ok.

nvidia 190.18.03 + 2.6.31-5-generic is no go.

---

### Post by kingborel on 2009-08-03
Woo, new kernel means suspend works again (hibernate still not working).

Unfortunatly, it broke virtualbox-ose (as expected) and I can't get it to rebuild :(

---

### Post by budluva04 on 2009-08-04
> **kingborel said:**
> Woo, new kernel means suspend works again (hibernate still not working).

Unfortunatly, it broke virtualbox-ose (as expected) and I can't get it to rebuild :(

i couldn't get vbox to run after either...but i did get it working with
```

$ sudo modprobe vboxdrv
```

then it complained i couldn't load the network device eth0 so it suggested.. 
```

$ sudo modprobe vboxnetflt
```

all is working now

---

### Post by caecusum on 2009-08-04
Did this kernel break Intel 3945 wireless for anyone else?

---

### Post by MacUntu on 2009-08-04
Nope, but that doesn't mean everything's alright. I've seen it more than once that IPW3945 worked on some machines and didn't work on others.

---

### Post by dr_kabuto on 2009-08-04
Hi,
with the latest 2.6.31-4 and .31-5 i get this error: "Error 13: invalid or unsupported executable format". Is anyone of you affected or I should file bug in LP?

Thanks!

---

### Post by pressureman on 2009-08-05
> **caecusum said:**
> Did this kernel break Intel 3945 wireless for anyone else?

I have an Intel 5300 wireless (Thinkpad T500) which works at first, but then just stops after a while, for no apparent reason.

---

### Post by taavikko on 2009-08-05
> **taavikko said:**
> And once again, nvidia module failed to build upon the arrival of the new kernel :)


Pheww... Finally can restart desktop with this new kernel,
reinstalled nvidia-180-kernel-source and run dkms {build,install} and it worked :)


```
devil@core7:~$ dkms status
nvidia, 185.18.14, 2.6.31-4-generic, x86_64: installed
devil@core7:~$ sudo dkms build -m nvidia -v 185.18.14 -k 2.6.31-5-generic

Kernel preparation unnecessary for this kernel.  Skipping...
applying patch drm_agp_memory-2.6.31.patch...patching file nv-i2c.c
patching file os-agp.c


Building module:
cleaning build area....
make KERNELRELEASE=2.6.31-5-generic module KERNDIR=/lib/modules/2.6.31-5-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/2.6.31-5-generic/build.....
cleaning build area....

DKMS: build Completed.
devil@core7:~$ sudo dkms install -m nvidia -v 185.18.14 -k 2.6.31-5-generic

nvidia.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-5-generic/updates/dkms/

depmod....

DKMS: install Completed.
devil@core7:~$ dkms status
nvidia, 185.18.14, 2.6.31-4-generic, x86_64: installed
nvidia, 185.18.14, 2.6.31-5-generic, x86_64: installed
devil@core7:~$

```

And now I can see the new kdm matching air theme :D

---

### Post by paul_in_london on 2009-08-05
> Pheww... Finally can restart desktop with this new kernel,
reinstalled nvidia-180-kernel-source and run dkms {build,install} and it worked 


When I got round to updating my minimal install yesterday, the existing nvidia module (185.18.14) installed ok with the new kernel (2.6.31-5-generic).

What happened previously, with my main karmic install (which uses various ppas), was that a simultaneous update of the nvidia driver (from 190.18 to 190.18.03) and kernel (from 2.6.31-RC5 to 2.6.31-5-generic) went wrong. There was a segfault or something. Can't remember exactly. Wasn't initially able to get 2.6.31-5-generic to boot with 190.18.03, but when I reinstalled 2.6.31-5-generic etc. the dkms build of 190.18.03 worked ok. :)

---

