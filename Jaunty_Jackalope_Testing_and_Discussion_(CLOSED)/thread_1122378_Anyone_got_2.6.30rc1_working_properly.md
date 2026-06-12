---
title: "Anyone got 2.6.30rc1 working properly?"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Xgen on 2009-04-11
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")
Tried it, but can't install the latest nvidia 173 driver...back to 2.6.29...

---

### Post by Starks on 2009-04-11
Intel wireless (iwl3945) seems to be broken.

---

### Post by MacUntu on 2009-04-11
Unload and reload it - should work.

---

### Post by paul_in_london on 2009-04-11
Not working for me unfortunately:

```
paul@jaunty-sdb:~/2.6.30$ cat /var/lib/dkms/nvidia/185.19/build/make.log
DKMS make.log for nvidia-185.19 for kernel 2.6.30-020630rc1-generic (i686)
Sat Apr 11 17:02:33 BST 2009
NVIDIA: calling KBUILD...
make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.30-020630rc1-generic/build SUBDIRS=/var/lib/dkms/nvidia/185.19/build modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /var/lib/dkms/nvidia/185.19/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia/185.19/build/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia/185.19/build
  cc -Wp,-MD,/var/lib/dkms/nvidia/185.19/build/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -Iinclude  -I/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include -include include/linux/autoconf.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I/var/lib/dkms/nvidia/185.19/build -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.19\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /var/lib/dkms/nvidia/185.19/build/.tmp_nv.o /var/lib/dkms/nvidia/185.19/build/nv.c
In file included from include/linux/bitops.h:17,
                 from include/linux/kernel.h:15,
                 from include/linux/sched.h:52,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/185.19/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/185.19/build/nv.c:14:
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/bitops.h: In function ‘set_bit’:
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/bitops.h:64: warning: pointer of type ‘void *’ used in arithmetic
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/bitops.h: In function ‘clear_bit’:
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/bitops.h:102: warning: pointer of type ‘void *’ used in arithmetic
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/bitops.h: In function ‘change_bit’:
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/bitops.h:178: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/list.h:6,
                 from include/linux/preempt.h:11,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:54,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/185.19/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/185.19/build/nv.c:14:
include/linux/prefetch.h: In function ‘prefetch_range’:
include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/185.19/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/185.19/build/nv.c:14:
include/linux/sched.h: In function ‘object_is_on_stack’:
include/linux/sched.h:2119: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/io.h:22,
                 from include/linux/pci.h:54,
                 from /var/lib/dkms/nvidia/185.19/build/nv-linux.h:86,
                 from /var/lib/dkms/nvidia/185.19/build/nv.c:14:
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/io.h: In function ‘writeq’:
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/io.h:70: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/dma-mapping.h:7,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/pci.h:129,
                 from include/linux/pci.h:1098,
                 from /var/lib/dkms/nvidia/185.19/build/nv-linux.h:86,
                 from /var/lib/dkms/nvidia/185.19/build/nv.c:14:
include/linux/scatterlist.h: In function ‘sg_virt’:
include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used in arithmetic
In file included from /var/lib/dkms/nvidia/185.19/build/nv-linux.h:113,
                 from /var/lib/dkms/nvidia/185.19/build/nv.c:14:
include/linux/highmem.h: In function ‘zero_user_segments’:
include/linux/highmem.h:147: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:147: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:147: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:147: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:150: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:150: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:150: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:150: warning: pointer of type ‘void *’ used in arithmetic
/var/lib/dkms/nvidia/185.19/build/nv.c: In function ‘nvos_proc_create’:
/var/lib/dkms/nvidia/185.19/build/nv.c:591: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/185.19/build/nv.c:592: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/185.19/build/nv.c:593: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/185.19/build/nv.c:613: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/185.19/build/nv.c:627: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/185.19/build/nv.c:638: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/185.19/build/nv.c:648: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/185.19/build/nv.c:658: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/185.19/build/nv.c:669: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/185.19/build/nv.c:676: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/var/lib/dkms/nvidia/185.19/build/nv.c: In function ‘nvos_proc_add_warning_file’:
/var/lib/dkms/nvidia/185.19/build/nv.c:703: error: ‘struct proc_dir_entry’ has no member named ‘owner’
make[3]: *** [/var/lib/dkms/nvidia/185.19/build/nv.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia/185.19/build] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2
paul@jaunty-sdb:~/2.6.30$ 

```

---

### Post by plun on 2009-04-11
[QUOTE]> **paul_in_london said:**
> Not working for me unfortunately:

You must patch the nVidia driver

**Message No 5**

[http://www.nvnews.net/vbulletin/showthread.php?t=131138](http://www.nvnews.net/vbulletin/showthread.php?t=131138)

;)

---

### Post by go7Ul1ai on 2009-04-11
Doesn't work for me, I get up to GDM but can't log in or do anything else.

---

### Post by plun on 2009-04-11
> **lee.jarratt said:**
> Doesn't work for me, I get up to GDM but can't log in or do anything else.

Well it works....

sudo sh for Ubuntu.

---

### Post by paul_in_london on 2009-04-11
Hmm. Thanks Plun.

I didn't have this problem with 2.6.29.1 though.

I was able to upgrade seamlessly to 185.19 via [https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa) without any problems when I was already running 2.6.29.1

I didn't use the Nvidia installer and I didn't need to patch anything, but the page you pointed me to talks about the need to patch for 2.6.29 as well as 2.6.30

Is there a way to get it to work without using the Nvidia installer? :confused:

---

### Post by plun on 2009-04-11
> **paul_in_london said:**
> 
Is there a way to get it to work without using the Nvidia installer? :confused:

Nope, I cannot find anyway using a repo
The problem is "owner" during install and it must be patched.

after you have patched you will have a new custom package to install with sudo sh.

---

### Post by DougieFresh4U on 2009-04-11
[FONT="Comic Sans MS"]Not to "hijack" thread, but does .30 work with 'fglrx'' ATI, as .29 doesn't?[/FONT]

---

### Post by plun on 2009-04-11
> **DougieFresh4U said:**
> [FONT="Comic Sans MS"]Not to "hijack" thread, but does .30 work with 'fglrx'' ATI, as .29 doesn't?[/FONT]

No idea, I am a nVidia freak..;)

The Unofficial ATI driver place again

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by zika on 2009-04-11
AMD Phenom X3, ATI HD3650 (radeon driver), 3G RAM, works like a charm!
[http://ubuntuforums.org/showpost.php?p=7039928&postcount=326](http://ubuntuforums.org/showpost.php?p=7039928&postcount=326)

---

### Post by paul_in_london on 2009-04-11
Thanks again Plun.

I'm still confused that, despite the comments on this page [http://www.nvnews.net/vbulletin/showthread.php?t=131138](http://www.nvnews.net/vbulletin/showthread.php?t=131138), 185.19 works for me with 2.6.29.1 but not with 2.6.30rc1

---

### Post by DougieFresh4U on 2009-04-11
Would some one please point me to .30 .deb or repo please?
Thanks, Dougie :p

---

### Post by jfernyhough on 2009-04-11
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc1/)

It's also in the first post. :wink:

I'm always nervous about touching early kernel rc's...

---

### Post by paul_in_london on 2009-04-11
Yep, that's where I picked it up.

Install both of the "all" debs and both of the debs for your architecture (i.e. 4 debs altogether).

This apparently won't work for me unless I patch the nvidia 185.19 driver, although I don't understand why this wasn't an issue with 2.6.29.1

---

### Post by cubeist on 2009-04-11
I wonder if the nvidia drivers fail on libdrm as the ati drivers do in 2.6.29 and forward? Has anyone been able to pull up a log from the 2.6.30 to see what is failing for nvidias?

---

### Post by paul_in_london on 2009-04-11
See my earlier post listing the contents of /var/lib/dkms/nvidia/185.19/build/make.log and this page [http://www.nvnews.net/vbulletin/showthread.php?t=131138](http://www.nvnews.net/vbulletin/showthread.php?t=131138), which says that 185.19 needs to be patched for both 2.6.29 and 2.6.30

---

### Post by DougieFresh4U on 2009-04-11
Thanks for the links.

Yikes!!!
All went good until I rebooted and clicked 'hardware drivers'. Installed 'fglrx' and rebooted, first sign of trouble was no 'loading bar' and nothing after that. 
So retreat  back to .28 (with tail between my legs) :p

---

### Post by cywhale on 2009-04-11
Hmm, maybe I'm missing something? 
Installing and booting linux-image...generic...i386.deb and linux-headers...all I get a totally distorted screen/Xorg with .29 and a nice looking but not responding to keyboard (mouse moveable) Xorg/GDM on my Travelmate C110/Intel 855GM /w EXA and UXA?

---

### Post by ronacc on 2009-04-12
I installed the 2.6.30-rc1 kernel and patched nvidia driver , everything seems fine except I've lost my wireless (rtl8185) which was working flawlessly with .28 and .29 .

---

### Post by DougieFresh4U on 2009-04-13
I do not know what I did wrong, but here goes:
When I first downloaded .debs and rebooted, no progress bar (strange) but after a few seconds I got login screen and logged in ok. took a few minutes before wireless was picked up and connected (strange). I then tried to install 'fglrx' and rebooted and all I got  was blank screen. Rebooted into .28 kernel and removed 'fglrx', rebooted and got blank screen again. Reboot back into .28 again and went to 'Synaptic' and completely removed the .30 kernel rebooted, this time into .29 kernel and reinstalled the .30 kernel. All I get after grub window is blank screen. Tried recovery for .30 and it scrolls a bit of info then stops and nothing  workable and have to reboot.
I do not have a clue as to what is going on and feel completely lost on this.
Any suggestions would be great.

---

### Post by zika on 2009-04-13
> **cywhale said:**
> Installing and booting linux-image...generic...i386.deb and linux-headers...
You need 3 files:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc1/linux-headers-2.6.30-020630rc1_2.6.30-020630rc1_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc1/linux-headers-2.6.30-020630rc1_2.6.30-020630rc1_all.deb")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc1/linux-headers-2.6.30-020630rc1-generic_2.6.30-020630rc1_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc1/linux-headers-2.6.30-020630rc1-generic_2.6.30-020630rc1_i386.deb")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc1/linux-image-2.6.30-020630rc1-generic_2.6.30-020630rc1_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc1/linux-image-2.6.30-020630rc1-generic_2.6.30-020630rc1_i386.deb")
(in that order preferably)

---

### Post by Xgen on 2009-04-19
I managed to get nvidia173.14.18 working with rc1, and now rc2. No real problems, but bootup hangs for 25 seconds while searching for nvidia173.14.16. It fails, then continues on and succeeds with the Jaunty boot process. Don't expect a solution, but curious why it would search for that driver. Note: reinstalled a modified nvidia173.14.16 to test, but still hangs.

---

### Post by jerrylamos on 2009-04-19
2.6.30-rc2 is running on an IBM Thinkpad R31 with integrated i830 graphics and an IBM ThinkCentre A30 with integrated i845 graphics.  Both these are slow (!) with full screen YouTube video.  2.6.30rc2 seems to help a bit.

Jerry

---

### Post by mainalisuyog on 2009-04-19
How about broadcom wireless? I got nvidia working, but broadcom wireless doesnt work. any fix for it?

---

