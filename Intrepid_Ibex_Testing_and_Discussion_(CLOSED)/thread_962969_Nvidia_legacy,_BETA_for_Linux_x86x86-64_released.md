---
title: "Nvidia legacy, BETA for Linux x86/x86-64 released"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by solitaire on 2008-10-29
Just been email this info:

  		[B]
96.43.09 (legacy, BETA) for Linux x86/x86-64 released[/B] 			
[http://www.nvnews.net/vbulletin/showthread.php?t=122139](http://www.nvnews.net/vbulletin/showthread.php?t=122139)


**71.86.07 (legacy, BETA) for Linux x86/x86-64 released** 			
[http://www.nvnews.net/vbulletin/showthread.php?t=122140](http://www.nvnews.net/vbulletin/showthread.php?t=122140)

I Hope these work...

I'm gonna Update the 96. Drivers NOW!

---

### Post by Awperator on 2008-10-29
Works for me on 8.10 so far!!!

I'll update on my progress

Updates so far:
 - Random bugs. The terminal does not work. Some windows don't have borders (firefox download window).
 - Many issues. Terminal has only a white window, can't see typed in text. Pop up windows are blank
 - White terminal and white popups fixed by disabling desktop effects.

---

### Post by solitaire on 2008-10-29
Not working for me!

I just get a blank screen when it gets to the login screens. I can login but screen is blank! :(

Ah well I'll send in a error report and see what they say :D

---

### Post by Manasia on 2008-10-29
THis update broke my kernel (2.6.27) I am going to install the update to an older kernel and see if I get shown some love.

---

### Post by Manasia on 2008-10-29
Nvidia driver does not work on my external device. Man that sucks.

---

### Post by Awperator on 2008-10-29
> **Manasia said:**
> THis update broke my kernel (2.6.27) I am going to install the update to an older kernel and see if I get shown some love.

I'm running 2.6.27-7 and it works fine for me. What exactly happened?

---

### Post by Manasia on 2008-10-29
> **Awperator said:**
> I'm running 2.6.27-7 and it works fine for me. What exactly happened?

I reinstalled the module, and it is working, but it does not work with my DVI output :-(. 

I use my box on a 42" HD TV, and the new driver seems to work only for SVGA out.

---

### Post by cjchand on 2008-10-29
> **Awperator said:**
> Works for me on 8.10 so far!!!

I'll update on my progress

Updates so far:
 - Random bugs. The terminal does not work. Some windows don't have borders (firefox download window).
 - Many issues. Terminal has only a white window, can't see typed in text. Pop up windows are blank
 - White terminal and white popups fixed by disabling desktop effects.

Solution for the missing title bars and white windows is here:
[http://www.nvnews.net/vbulletin/showthread.php?p=1826952#post1826952]("http://www.nvnews.net/vbulletin/showthread.php?p=1826952#post1826952").

In short, add "Option "AddARGBGLXVisuals" "True"" to your xorg.conf and restart X. 

Cheers,
CJC

---

### Post by Awperator on 2008-10-29
> **Manasia said:**
> I reinstalled the module, and it is working, but it does not work with my DVI output :-(. 

I use my box on a 42" HD TV, and the new driver seems to work only for SVGA out.

That's odd because I have it on DVI out on my vid card. I wouldn't know where to help you out at. Maybe you should try submitting a automatic bug report to Nvidia?
[http://www.nvnews.net/vbulletin/showthread.php?t=46678]("http://www.nvnews.net/vbulletin/showthread.php?t=46678")

---

### Post by Megatog615 on 2008-10-30
Anyone have a .deb for these yet?

---

### Post by loomsen on 2008-10-30
> **Manasia said:**
> I reinstalled the module, and it is working, but it does not work with my DVI output :-(. 

I use my box on a 42" HD TV, and the new driver seems to work only for SVGA out.

Maybe because both drivers above are for LEGACY?

The newest driver for 8K and above cards is (somewhat misleading)

177.61.02 (OpenGL 3.0 BETA) 

BETA isn't written in Capitals just for fun tho, you should have your card working, and more important. you should have some experience with editing xorg and fixin X from terminal...

[Official BETA-rel Announcement](http://www.nvnews.net/vbulletin/showthread.php?t=121763)

---

### Post by Manasia on 2008-10-30
> **Awperator said:**
> That's odd because I have it on DVI out on my vid card. I wouldn't know where to help you out at. Maybe you should try submitting a automatic bug report to Nvidia?
[http://www.nvnews.net/vbulletin/showthread.php?t=46678]("http://www.nvnews.net/vbulletin/showthread.php?t=46678")

I thought the same thing, but I do not get an error report. 

I am going to report it to the Nvidia team though. Thanks for the reply.

---

### Post by Manasia on 2008-10-30
> **loomsen said:**
> Maybe because both drivers above are for LEGACY?

The newest driver for 8K and above cards is (somewhat misleading)

177.61.02 (OpenGL 3.0 BETA) 

BETA isn't written in Capitals just for fun tho, you should have your card working, and more important. you should have some experience with editing xorg and fixin X from terminal...

[Official BETA-rel Announcement](http://www.nvnews.net/vbulletin/showthread.php?t=121763)

I know how to fix X from a term, and I read the announcement. I am not upset or anything, just reporting the fact that I could not get external video. 

If anyone else has had any dual monitor or DVI-OUT success on a Geforce3 card please private message me or post.

---

### Post by Jæd on 2008-10-30
I tried to install this, and got a compile error &#8211; see below

This was trying : NVIDIA-Linux-x86-96.43.09-pkg1.run

```
make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=
   /tmp/selfgz28892/NVIDIA-Linux-x86-96.43.09-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";    \
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";    \
       echo;                                \
       /bin/false)
   mkdir -p /tmp/selfgz28892/NVIDIA-Linux-x86-96.43.09-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz28892/NVIDIA-Linux-x86-96.43.09-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz28892/NVIDIA-Linux-x86-96.43.0
   9-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz28892/NVIDIA-Linux-x86-96.43.09-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -i
   nclude include/linux/autocon
```Does anyone have a how-to for this...?. Thanks...!

---

### Post by Elfy on 2008-10-30
I had some problems - although not that one.

Solved by following the nvidia instructions for > Debian GNU/Linux or [K]Ubuntu with Xorg 7.x on this page [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

but I have problems with the driver it gives me this - I'm not usre whether anything on that page caused the issue.

---

### Post by Manasia on 2008-10-30
> **Jæd said:**
> I tried to install this, and got a compile error &#8211; see below

This was trying : NVIDIA-Linux-x86-96.43.09-pkg1.run

```
make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=
   /tmp/selfgz28892/NVIDIA-Linux-x86-96.43.09-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";    \
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";    \
       echo;                                \
       /bin/false)
   mkdir -p /tmp/selfgz28892/NVIDIA-Linux-x86-96.43.09-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz28892/NVIDIA-Linux-x86-96.43.09-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz28892/NVIDIA-Linux-x86-96.43.0
   9-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz28892/NVIDIA-Linux-x86-96.43.09-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -i
   nclude include/linux/autocon
```Does anyone have a how-to for this...?. Thanks...!

I got this same error with a segmentation fault dump, in the log file. I have had several seg faults since upgrading, anyone else with the same problem?

---

