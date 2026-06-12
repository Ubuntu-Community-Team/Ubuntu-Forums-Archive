---
title: "fglrx on 2.6.31-4-rt and 2.6.31-9-generic"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-09-04
i dont know if anyones struggling with fglrx on the latest generic and rt kernels but i've bodged together a version that builds on them both. i dont know if it actually works properly so  use them at your own peril :)
if they dont work it may well be the binary part so unlikely to be fixed until ati do :(
Packages, debdiffs, etc at ppa,

[https://launchpad.net/~dinxter/+archive/ppa](https://launchpad.net/~dinxter/+archive/ppa)

versions,
fglrx, 8.632, 2.6.31-9-generic, x86_64: installed 
fglrx, 8.632, 2.6.31-4-rt, x86_64: installed

---

### Post by andrek on 2009-09-04
I'm going to try it right now.

---

### Post by dinxter on 2009-09-04
> **andrek said:**
> I'm going to try it right now.
careful now... :)

---

### Post by ranch hand on 2009-09-04
Just to make sure - this is supposed to work on 2.6.31-9 right?  I ask because looking at the stuff on launchpad it appears to be for the rt kernal.

I really do not know what the difference is so I thought I better check as this -9 seems a litttle tender.

I do have installs to burn though so I would like to try it.

---

### Post by andrek on 2009-09-04
Well, just like always.

```

(...)
Setting up fglrx-kernel-source (2:8.632-0ubuntu2~dinxter4) ...
Adding Module to DKMS build system
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.31-5-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.632/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module flrx in the DKMS tree.
You must run a dkms build for kernel 2.6.31-5-generic (i686) first.

Setting up xorg-driver-fglrx (2:8.632-0ubuntu2~dinxter4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

---

### Post by dinxter on 2009-09-04
> **andrek said:**
> Well, just like always.

```

(...)
Setting up fglrx-kernel-source (2:8.632-0ubuntu2~dinxter4) ...
Adding Module to DKMS build system
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.31-5-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.632/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module flrx in the DKMS tree.
You must run a dkms build for kernel 2.6.31-5-generic (i686) first.

Setting up xorg-driver-fglrx (2:8.632-0ubuntu2~dinxter4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

unforunately since i only have access to the 2.6.31-9 and 2.6.31-4-rt kernels, the latest karmic ones, these might be the only kernels it works for. i cant test 2.6.31-5-generic at the moment, i may look into that tomorrow though

---

### Post by dinxter on 2009-09-04
actually, only 2.6.31-9 is available in pool now so its probably more effort than its worth to build my own 2.6.31-5 version, i'll probably just stick with the up to date karmic ones. though if you post your log on a failed build i'll of course try to help!

---

### Post by dinxter on 2009-09-04
> **ranch hand said:**
> Just to make sure - this is supposed to work on 2.6.31-9 right?  I ask because looking at the stuff on launchpad it appears to be for the rt kernal.

I really do not know what the difference is so I thought I better check as this -9 seems a litttle tender.

I do have installs to burn though so I would like to try it.

only the last version added an rt compatibility patch, until then it was 2.6.31-9-generic only.

---

### Post by andrek on 2009-09-04
I have just updated to -9 and the output is just the same. Getting an indentical error.

I'd share my /var/lib/dkms/fglrx/8.632/build/make.log file, but i'm unable to start xserver.. My xorg.conf is totally empty (always was on karmic here) and I have removed your drivers - I guessed it would start with VESA drivers but it doesn't.

---

### Post by andrek on 2009-09-04
Ok, I got it running on VESA drivers, here's the make.log file :
```
Fri Sep  4 21:03:59 CEST 2009
sh: /var/lib/dkms/fglrx/8.632/build: Permission denied
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.31-9-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.632/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-9-generic'
  CC [M]  /var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:41:2: error: #error unknown or undefined architecture configured
In file included from /var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:169:
/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.h:607:1: warning: "pgprot_writecombine" redefined
In file included from /usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/irqflags.h:61,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:91:
/usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/pgtable_types.h:282:1: warning: this is the location of the previous definition
In file included from /var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:169:
/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.h:611:1: warning: "pgprot_noncached" redefined
In file included from include/linux/mm.h:38,
                 from /usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/pci.h:4,
                 from include/linux/pci.h:1112,
                 from /var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:98:
/usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/pgtable.h:12:1: warning: this is the location of the previous definition
In file included from /var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:431:
/var/lib/dkms/fglrx/8.632/build/2.6.x/drm_proc.h: In function ‘FGLDRM__vma_info’:
/var/lib/dkms/fglrx/8.632/build/2.6.x/drm_proc.h:497: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 5 has type ‘phys_addr_t’
/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c: In function ‘KCL_SetPageCache_Array’:
/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:1230: warning: unused variable ‘ret’
/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:1229: warning: unused variable ‘i’
make[2]: *** [/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.632/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-9-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
```

---

### Post by dinxter on 2009-09-04
> **andrek said:**
> Ok, I got it running on VESA drivers, here's the make.log file :
```
Fri Sep  4 21:03:59 CEST 2009
sh: /var/lib/dkms/fglrx/8.632/build: Permission denied
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.31-9-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.632/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-9-generic'
  CC [M]  /var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:41:2: error: #error unknown or undefined architecture configured
In file included from /var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:169:
/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.h:607:1: warning: "pgprot_writecombine" redefined
In file included from /usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/irqflags.h:61,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:91:
/usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/pgtable_types.h:282:1: warning: this is the location of the previous definition
In file included from /var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:169:
/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.h:611:1: warning: "pgprot_noncached" redefined
In file included from include/linux/mm.h:38,
                 from /usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/pci.h:4,
                 from include/linux/pci.h:1112,
                 from /var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:98:
/usr/src/linux-headers-2.6.31-9-generic/arch/x86/include/asm/pgtable.h:12:1: warning: this is the location of the previous definition
In file included from /var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:431:
/var/lib/dkms/fglrx/8.632/build/2.6.x/drm_proc.h: In function &#8216;FGLDRM__vma_info&#8217;:
/var/lib/dkms/fglrx/8.632/build/2.6.x/drm_proc.h:497: warning: format &#8216;%08lx&#8217; expects type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;phys_addr_t&#8217;
/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c: In function &#8216;KCL_SetPageCache_Array&#8217;:
/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:1230: warning: unused variable &#8216;ret&#8217;
/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.c:1229: warning: unused variable &#8216;i&#8217;
make[2]: *** [/var/lib/dkms/fglrx/8.632/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.632/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-9-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
```

ah, /usr/src/linux-headers-2.6.31-9-generic/include/linux/autoconf.h should define the arch. fglrx is looking for CONFIG_X86_PC to be defined for x86, it should be looking for CONFIG_X86_GENERIC it seems. 
if your on x86 try adding 
#define CONFIG_X86_PC 
just after 
#include <linux/autoconf.h>

in the file,
/usr/src/fglrx-8.632/firegl_public.c 
and rerun dkms
if that works i'll fix that up in the ppa

---

### Post by dinxter on 2009-09-04
if
#ifdef CONFIG_X86_GENERIC
#define CONFIG_X86_PC
#endif
works, i'll just add that so x86 systems work, anyone tried amd64? it should at least build ok

---

### Post by andrek on 2009-09-04
How can I "rerun" DKMS?

edit:
Ok, I did 
*sudo dkms build -m fglrx -v 8.632 -k `uname -r` *
and it gave me
[I](...)
DKMS: build Completed.[/I]
Now i'm going to reboot and check whether it works..

edit2:
Nope, same old.. thing. No errors at all, it just doesn't go any further than the loading ( usplash i guess ). It shows some mini-ubuntu logos with some green lines ( artifects I guess ), nothing more, but the system works as I can hear the "welcome" sound. I can switch to tty1 with no problems, too.

---

### Post by dinxter on 2009-09-04
sounds like the binary part is just plain broken at the moment which is a shame, you could maybe try it without usplash, it can cause problems. or even starting it from tty as your user
$/etc/init.d/gdm stop
$startx
but i doubt it'll help somehow

---

### Post by DougieFresh4U on 2009-09-04
I tried on my 64 bit and when I boot it gets to where login screen SHOULD be, but all I get is a pretty thin blue/purple line across the top of my screen.
Of course this machine being a multi boot, my grub menu doesn't show the recovery line for each kernel installed, so kind of stuck at the moment, using my other Karmic partition.

---

### Post by dinxter on 2009-09-04
> **DougieFresh4U said:**
> I tried on my 64 bit and when I boot it gets to where login screen SHOULD be, but all I get is a pretty thin blue/purple line across the top of my screen.
Of course this machine being a multi boot, my grub menu doesn't show the recovery line for each kernel installed, so kind of stuck at the moment, using my other Karmic partition.
should be able to press e to edit the grub entries, remove quiet and splash options and replace them with single. that should get you happily to recovery mode. does sound like i wont be bothering with ati for a few months by the sounds of it

---

### Post by andrek on 2009-09-04
After doing

sudo /etc/init.d/gdm stop
startx

it tries to start xserver, but with no success. (same as before - it shows some artifacts)
However, I can see some errors on tty1 :

```
(EE) fglrx(0): PPLIB: PPLIB is not initialized!
(EE) fglrx(0): PPLIB: swLPPLibNotifyEventToPPLib() failed!
(EE) fglrx(0):        ulEventType = 0000000c , ulEventData = 00000001
(EE) fglrx(0): PPLIB: PPLIB is not initialized!
(EE) fglrx(0): PPLIB: swLPPLibNotifyEventToPPLib() failed!
(EE) fglrx(0):        ulEventType = 00000002 , ulEventData = 00000000
(EE) fglrx(0): Failed to disable interrupts. Errorcode -22
(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
```

I'm running x86 karmic on Dell Studio 1555 with ATI 4570, btw.

and one more thing - how come it is working on your x86-64 while it does not on x86? Is it that huge difference for driver binaries? I'll try to install new karmic x86-64 tommorow.


***edit:***

Thanks for your effort, anyway.

---

### Post by dinxter on 2009-09-04
it builds on x86 and 64 now, i wouldnt be running it til at least monday, but i doubt i'll bother by the sounds of it. 
the binary part looks broken and theres nothing that can be done about that. if anyone has any luck with a newer fglrx i'll try updating but its an ati issue now, it needs a proprietary update!

---

### Post by dinxter on 2009-09-04
oh well, it was worth a try :( hope the open source ati is working well enough for everyone

---

### Post by ranch hand on 2009-09-04
I just realized that it would be a waste of time for me to fool with this.  My 2400 Pro is not covered by any driver that I know of anyway.

---

### Post by DougieFresh4U on 2009-09-04
Just tried it on a fresh install 64 bit. Loading bar finishes and then I am left with a black screen.

---

### Post by DougieFresh4U on 2009-09-04
Choosing the recovery from grub, what would I type to remove this fglrx to get up and running again?
Thanks.
Could also reinstall as it was a reinstall about an hour ago, but would rather salvage this one.

---

### Post by trebach on 2009-09-04
> **DougieFresh4U said:**
> Choosing the recovery from grub, what would I type to remove this fglrx to get up and running again?
Thanks.
Could also reinstall as it was a reinstall about an hour ago, but would rather salvage this one.

Step 1: Set xorg.conf back to the open source driver.
```
sudo nano /etc/X11/xorg.conf
```
In the "Devices" section,  on the Driver line, change it from "fglrx" back to "radeon".

Step 2: Uninstall fglrx.
```
sudo apt-get purge fglrx*
```

Restart and all should be right with the world.

---

### Post by DougieFresh4U on 2009-09-04
> **trebach said:**
> Step 1: Set xorg.conf back to the open source driver.
```
sudo nano /etc/X11/xorg.conf
```
In the "Devices" section,  on the Driver line, change it from "fglrx" back to "radeon".

Step 2: Uninstall fglrx.
```
sudo apt-get purge fglrx*
```

Restart and all should be right with the world.

Thanks so much for your words of wisdom. Unfortunately, my grub now isn't showing the 'recovery' lines. So no way to get to recovery console via grub.

---

### Post by trebach on 2009-09-05
> **DougieFresh4U said:**
> Thanks so much for your words of wisdom. Unfortunately, my grub now isn't showing the 'recovery' lines. So no way to get to recovery console via grub.

When it starts X, hit Ctrl-Alt-F1 to go to terminal, log in, and then follow the steps.

---

### Post by dinxter on 2009-09-05
what a diference a day makes :) 

[https://launchpad.net/ubuntu/+source/fglrx-installer](https://launchpad.net/ubuntu/+source/fglrx-installer)

            **[2:8.660-0ubuntu1]("https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.660-0ubuntu1")**     
                                       Published        in        [karmic]("https://launchpad.net/ubuntu/karmic/+source/fglrx-installer")-release                        10 hours ago                                  
           fglrx-installer (2:8.660-0ubuntu1) karmic; urgency=low

  * New upstream release.
    + Fix freeze on boot with purple and green ubuntu logos
      (LP: [#423711]("https://launchpad.net/bugs/423711"))
    + Fix boot failure due to DKMS change.  Sometimes X crashes as result.
      (LP: [#417617]("https://launchpad.net/bugs/417617"), [#413751]("https://launchpad.net/bugs/413751"))
    + Make fglrx compile with dkms on 2.6.30 and 2.6.31 for amd64
      (LP: [#410062]("https://launchpad.net/bugs/410062"))
    + Fix "Desktop effects could not be enabled" on HD 4850 and HD 4870
      (LP: [#417500]("https://launchpad.net/bugs/417500"), [#408633]("https://launchpad.net/bugs/408633"))
    + Provide support for 2.6.31 kernel
      (LP: [#413791]("https://launchpad.net/bugs/413791"))
    + Use Catalyst Control Center for display configuration
      (LP: [#410512]("https://launchpad.net/bugs/410512"))
    + Catalyst Control Center shows up in Apps > Accessories, should be in
      System > Administration > Display
      (LP: [#423670]("https://launchpad.net/bugs/423670"))

---

### Post by andrek on 2009-09-05
Wow, I hope this will fix my issues. I'll give it a try.

Works wonderfully. Thanks for notifying, dinxter!

---

### Post by DougieFresh4U on 2009-09-05
Simple question, but I need to know.
Once I have installed ppa, do I need to go to System>Administration>Hardware Drivers and activate fglrx?

---

### Post by dinxter on 2009-09-05
> **DougieFresh4U said:**
> Simple question, but I need to know.
Once I have installed ppa, do I need to go to System>Administration>Hardware Drivers and activate fglrx?

dont use ppa, its the old broken version, the new version is in the main repositories. 
System>Administration>Hardware Drivers
should work, if not you can change the driver to fglrx in xorg.conf

---

### Post by DougieFresh4U on 2009-09-05
> **dinxter said:**
> dont use ppa, its the old broken version, the new version is in the main repositories. 
System>Administration>Hardware Drivers
should work, if not you can change the driver to fglrx in xorg.conf

Good morning and thanks.
I have fresh Karmic 64 bit install. For some reason 'Hardware Driver' window is empty. It wasn't earlier. But then I almost used ppa. I installed it and packages then saw your post so I removed ppa and packages. Glad I didn't reboot or I would have had a mess.
Spec's: AMD Athlon 64x2 5200  ATI Radeon HD3200

---

### Post by dinxter on 2009-09-05
> **DougieFresh4U said:**
> Good morning and thanks.
I have fresh Karmic 64 bit install. For some reason 'Hardware Driver' window is empty. It wasn't earlier. But then I almost used ppa. I installed it and packages then saw your post so I removed ppa and packages. Glad I didn't reboot or I would have had a mess.
Spec's: AMD Athlon 64x2 5200  ATI Radeon HD3200
a mess indeed :) recovering from ati/nvidia driver failures eventually becomes like second nature on dev distributions, you often get a accidental tutorial on the grub command line too!

---

### Post by DougieFresh4U on 2009-09-05
Any idea why my Hardware Driver window is empty?

---

### Post by dinxter on 2009-09-05
i couldnt say for sure but jockey sometimes has drivers disabled when they are known to be broken, and fglrx was until today, so it may be that

---

### Post by DougieFresh4U on 2009-09-05
Working great here!! 2.6.31.9-generic (fresh, clean install)
Karmic 64 bit  ATI Radeon HD3200
Thanks dinxter

---

### Post by dinxter on 2009-09-05
> **DougieFresh4U said:**
> Working great here!! 2.6.31.9-generic
Karmic 64 bit  ATI Radeon HD3200
Thanks dinxter
good to hear, nothing to do with me though, credit to those due it :)

---

