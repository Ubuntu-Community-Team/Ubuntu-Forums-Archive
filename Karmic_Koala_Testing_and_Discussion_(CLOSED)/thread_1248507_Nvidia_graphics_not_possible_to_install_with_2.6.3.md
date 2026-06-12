---
title: "Nvidia graphics not possible to install with 2.6.31-1-rt."
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by daggedog on 2009-08-24
I have tried with the .run package from [www.nvidia.com]("http://www.nvidia.com") and the other method, but it is only possible to install with the generic kernel. I read somewhere that  a patch could make2.6.31-1-rt work with nvidia, but how do I add that patch?

---

### Post by trulan on 2009-08-24
I have it sort of working on mine, but I'm not sure exactly how I got there.  My screen resolution is great and the drivers seem to load successfully, but they do not appear to be installed and I can't use the nvidia settings utility.

But, 2.6.31-2-rt is now in the repo, so give that a try.  I intend to try to get the nvidia drivers installed properly as soon as I get a chance.

---

### Post by trulan on 2009-08-24
Oh, I know how I got it working - I installed the generic kernel as well.  I had forgotten why - but I believe it was to get graphics working properly.  I've only booted up on it a few times, but it's installed.  Probably not the 'patch' you are looking for...

Edit:  I'll just add on to my post here:
I don't know if the NVidia drivers are working for me or not.  I thought they were because my screen resolution is at 1280x1024, and on Jaunty the only way to get it above 800x600 is to install the drivers.  xorg.conf shows the nvidia driver but none of the setup utilities work and they do not show as installed...

Attempting to install the NVidia drivers through Jockey (system/administration/hardware drivers) fails very quickly with no error message.  Attempting to install from the NVidia .run package, or with any of several make commands I have tried, always results in a failure to build the kernel module.

In /var/lib/dkms/nvidia/185.18.36/build/make.log, I find this:
```
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
```And farther down, lots of these:
```
warning: pointer of type &#8216;void *&#8217; used in arithmetic
```Is this suggesting I need to run several commands on the kernel source code, then compile the kernel myself, to get the drivers working?  That seems a little extreme...I'll post the whole log file if anybody wants to see it.

---

### Post by trulan on 2009-08-24
The bug and a patch, are here:
[U][https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/413296](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/413296)
[/U]I have not tested this yet.

Edit:
Tested this patch - I'm a newbie, so I easily could have messed up.  It appears to break something though.  The first time I applied it (after two failed attempts to do so) it looked like it was working - boot-up paused a bit, then the 'waiting' mouse pointer showed up (small, like it should be - this was after running on the nv drivers at ridiculously low resolution).  Then the system froze (first hard freeze I've had in Karmic BTW).  Next boot failed, and the system rebooted itself.  Subsequent boot-ups dumped me to the terminal login.

At any rate, I edited xorg.conf and told it to use the vesa drivers instead of nvidia, so at least my screen is back.  I think it had been defaulting to the vesa drivers all along, and the Nvidia ones never did load properly with the rt kernel.  But my screen is at 1280x1024 again, and I am happy for now.

---

### Post by daggedog on 2009-08-25
Thanks for the suggestions. I'm a newbie as well. I will try to paste the patch in the /home/user/ directory,
.emacs.d/backups/!var!lib!dkms!nvidia!185.18.29!build!nv-linux.h.~1~	2009-07-30 11:21:49.069661782 +0200
+++ /usr/src/nvidia-185.18.29/nv-linux.h	2009-07-30 11:38:44.857538204 +0200
@@ -721,7 +721,7 @@
 #define nv_up(lock)                     up(&lock)
 
 #if defined(CONFIG_PREEMPT_RT)
-#define NV_INIT_MUTEX(mutex) init_MUTEX(mutex)
+#define NV_INIT_MUTEX(mutex) semaphore_init(mutex)
 #else
 #if !defined(__SEMAPHORE_INITIALIZER) && defined(__COMPAT_SEMAPHORE_INITIALIZER)
 #define __SEMAPHORE_INITIALIZER __COMPAT_SEMAPHORE_INITIALIZER[unhandled content-type:application/pgp-signature]

---

### Post by Stochastic on 2009-08-26
Moved to Karmic Koala Development Forum.

---

### Post by daniel_cello on 2009-08-26
> **daggedog said:**
> I have tried with the .run package from [www.nvidia.com]("http://www.nvidia.com") and the other method, but it is only possible to install with the generic kernel. I read somewhere that a patch could make2.6.31-1-rt work with nvidia, but how do I add that patch?
 
Not sure how it fails for you but I got problems trying to install nvidia drivers using the "proprietary hardware driver" (?) that pops up after login to a freshly installed U.S.
 
I would get a complete freeze as the download started that it didn't recover from so I had to do a hard reset. The same freeze would occur when trying to update the installation, so I guess most ethernet activity will cause problems.
 
The answer (found in the forums) was to not use more than one core on my cpu. Not much point in buying a core2quad, but hopefully they will resolve the issues with the kernel-rt with an update... The magic commands that stopped the freeze for me was to add "nosmp, pnpbios=off, acpi=off, maxcpus=1" to the kernel options in grub. Not sure if this is your problem, but if it is the same solution should apply for you too.
 
(The thread that discusses the freeze can be found [here]("http://ubuntuforums.org/showthread.php?t=1138363").)

---

### Post by trulan on 2009-08-26
Thanks for the suggestion.  I'll check out that thread.

According to the bug linked above, this problem is specific to the .31 rt kernels.  From the bug report:
> the build fails due to undefined reference to init_MUTEX
The patch linked in the bug changes init_MUTEX to semaphore_init.  This still fails to build for me, and dumps me to a TTY if the nvidia drivers are selected in xorg.conf.

I have a single core AMD64, BTW.

---

### Post by UCanCallMeJesus on 2009-08-26
This may seem stupid but are you updating the grub menu.lst file so that it is the latest Kernel? I had to change the kernel version because I have a modified grub file. Then I installed Nvidia 185 no problems. I couldn't install Nvidia because my grub file was not updated.Good luck.

---

### Post by ram130 on 2009-08-27
same problem with ATI...i guess we just have to way til the next alpha release... Tried the method to install, says downloading then disappears. Tried direct install from ATI, system boots fine, but the screen shows a corrupt imagine(mainly black with colours across at the top), tried envy, but drops me to TTY. I think they are aware of this, by the beta release we should be good again. ma kernal version is  2.6.31-3-rt

---

### Post by hanzomon4 on 2009-08-27
I ok I feel better... I rolled my own RT kernels and the nvidia drivers just would not install. I'm glad that it's not just me (sorry). It must be something with the patch... I'll try building a 2.6.31 kernel without the patch to see if the drivers install.

---

### Post by UCanCallMeJesus on 2009-08-27
My kernel is vmlinuz-2.6.31-7-generic and I had no problem installing Nvidia 185. The driver works great. Why don't you go with the generic version?

---

### Post by trulan on 2009-08-27
> **UCanCallMeJesus said:**
> This may seem stupid but are you updating the grub menu.lst file so that it is the latest Kernel? I had to change the kernel version because I have a modified grub file. Then I installed Nvidia 185 no problems. I couldn't install Nvidia because my grub file was not updated.Good luck.
I fought with grub2 for quite a while.  I think we have come to a 'mutual understanding' and I have declared a temporary 'cease fire' with that particular piece of software. grub.cfg has been edited, believe me.

As I understand it, it's actually a regression due to the newest rt kernels.  When I installed Karmic alpha 3 the rt kernel was at 2.6.29.something.  The nvidia drivers will build on that kernel.  But with 2.6.31.1-rt, the init_MUTEX stuff was removed from the rt-preempt kernel patch, and the nvidia driver depended on that.  So until that is put back into the kernel, or until the driver is patched, it will fail to build.  I am not sure if the ATI driver is suffering from this same issue, or if it is another problem.

But the vesa driver gives me full resolution in Karmic (I'm sure in Jaunty it limited me to 800x600), so I don't even really need the nvidia driver.

> **UCanCallMeJesus said:**
> Why don't you go with the generic version?
Me personally?  Because the generic kernel will not run my audio recording interface (Presonus Firepod).  The real time kernel runs it incredibly well.  That being said, I do have the generic kernel installed and the nvidia drivers work fine on that.  Just not on the real time kernel.

---

### Post by dinxter on 2009-08-27
seems to be a one line change to MUTEX_init to semaphore_init in nv-linux.c
-#define NV_INIT_MUTEX(mutex) init_MUTEX(mutex)
+#define NV_INIT_MUTEX(mutex) semaphore_init(mutex)
builds and works fine here with that on 2.6.31-3-rt

---

### Post by trulan on 2009-08-27
Unfortunately that doesn't work for me.  I know I did a few things wrong before I changed that line of code so it might be my fault.  And 2.6.31-3-rt won't boot at all for me, though the previous versions boot OK.  Maybe it's time for a fresh install...

---

### Post by trulan on 2009-08-28
OK, I can report that changing that line in /usr/src/nvidia-185.18.36/nv-linux.h does indeed solve the problem.  The dkms build now completes both for 2.6.31-2-rt and for 2.6.31-3-rt.  The driver is working for me on 2.6.31-2-rt.

I am still unable to boot on 2.6.31-3-rt but that's another issue for another thread:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1249906](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1249906)

---

### Post by hanzomon4 on 2009-08-28
```

#define nv_init_lock(lock)              spin_lock_init(&lock)
#define nv_lock(lock)                   spin_lock(&lock)
#define nv_unlock(lock)                 spin_unlock(&lock)
#define nv_lock_irq(lock,flags)         spin_lock_irqsave(&lock,flags)
#define nv_unlock_irq(lock,flags)       spin_unlock_irqrestore(&lock,flags)
#define nv_down(lock)                   down(&lock)
#define nv_up(lock)                     up(&lock)

#if defined(CONFIG_PREEMPT_RT)
#[COLOR="Red"]**define NV_INIT_MUTEX(mutex) semaphore_init(mutex)**[/COLOR]
#else
#if !defined(__SEMAPHORE_INITIALIZER) && defined(__COMPAT_SEMAPHORE_INITIALIZER)
#define __SEMAPHORE_INITIALIZER __COMPAT_SEMAPHORE_INITIALIZER
#endif
#define NV_INIT_MUTEX(mutex)                       \

```

Thats the change I made still fails... were can I find an error log for this?

EDIT: Found a way... this is what I get when I try it manually 
```
mkdir -p .tmp_versions ; rm -f .tmp_versions/*
make -f scripts/Makefile.build obj=scripts/basic
(cat /dev/null; ) > scripts/basic/modules.order
make -f scripts/Makefile.build obj=.
(cat /dev/null; ) > modules.order
make -f scripts/Makefile.build obj=. missing-syscalls
make[3]: *** No rule to make target `missing-syscalls'.  Stop.
make[2]: *** [prepare0] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2

```

---

### Post by hanzomon4 on 2009-08-31
Any new info on this?

---

### Post by dinxter on 2009-08-31
cant replicate your problem unfortunately, if you can post your 
/var/lib/dkms/nvidia/185.18.36/build/make.log
after running 
dkms build -m nvidia -v 185.18.36 -k 2.6.31-3-rt
maybe something will become apparent

---

### Post by zatoichi0 on 2009-09-01
Seems to work on 2.6.31-3-rt, after applying the patch.

"Seems to work" because I just got it running - with some artifacts, but usable once loaded.

Same problem and solution for kqemu, BTW.

---

