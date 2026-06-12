---
title: "ATI binary driver working yet?"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by christian.convey on 2009-08-14
I've got a Radeon HD-4850 based card.  Anyone know if the proprietary driver is likely to work for it yet?

When I tried about a month ago, it installed okay, but I'd get a blank screen.

---

### Post by madjr on 2009-08-14
am too interested about ATI, but more on how **3D performance** dev is going on the **Open source driver**, since my card is not officially supported anymore..

---

### Post by XPM on 2009-08-14
I was wondering the same thing. I haven't been able to use 9.04 yet with my 4850x2

The opensource driver crashes after a few minutes of use...I think it overheats? 
Either way...Having tried all versions, I've given up.

Yeah, I could install newer kernels and do some hacks...sure
But I want a stock system that works out of the box.

---

### Post by descendent87 on 2009-08-14
I have a HD3200 and have 3D working using the opensource drivers on arch (using mesa and a lot of other stuff from git, not stable yet) and it's coming along very nicely.
The fglrx driver still doesn't officially work with anything newer than the 2.26.28 kernel (as far as i know), there are patches to get it working with 2.6.29 and 2.6.30, I don't know if ubuntu has patched their driver to work

---

### Post by dinxter on 2009-08-14
see [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/394985](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/394985)

---

### Post by efgevh on 2009-08-14
I updated sources and added the key for dinxter PPA. Then I sudo apt-get update, and then I installed the packages :
 
    * fglrx-amdcccle  
    * fglrx-kernel-source 
    * fglrx-modaliases I
    * libamdxvba1 
    * xorg-driver-fglrx 
  
After that since I didn't have no xorg.conf, I copied one from a jaunty partition which uses the open driver, and then I did 
aticonfig -initial 

Output said file was updated and I rebooted. Black screen. HD3870
How can I apply this patch the right way?

---

### Post by jerrylamos on 2009-08-15
I use Driver "vesa" because A4 boots to a black screen with the default.

Compaq Presario 3.33 gHz Celeron ati radeon Xpress 200

BTW, on some of my systems Driver "vesa" is faster if not much faster than the default ubuntu driver, particularly in KMS mode.....

Jaunty beats Karmic Alpha's hands down on my four test pc's with video graphics tests like gtkperf from synaptic.

Jerry

---

### Post by wayne_cat on 2009-08-15
> **jerrylamos said:**
> I use Driver "vesa" because A4 boots to a black screen with the default.

Compaq Presario 3.33 gHz Celeron ati radeon Xpress 200

BTW, on some of my systems Driver "vesa" is faster if not much faster than the default ubuntu driver, particularly in KMS mode.....

Jaunty beats Karmic Alpha's hands down on my four test pc's with video graphics tests like gtkperf from synaptic.

Jerry

You have tested the GTK performance with the vesa driver?

---

### Post by jerrylamos on 2009-08-15
A4 now booting O.K. with
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/kms](https://edge.launchpad.net/~ubuntu-x-swat/+archive/kms)
PPA radeon driver 1:6.12.99+git20090805

Black screen hang with the A4 CD driver.  Since it hung, I don't know what Xorg.0.log would have shown for the driver it was trying to use.  Booted in recovery, copied in an xorg.conf, specified Driver "vesa" and CD booted O.K.
So did the install with Driver "vesa".  Install booted O.K. with "vesa".

Updated to the PPA driver referenced above and booted O.K.

Runs O.K. with GtkPerf video graphics benchmark, 13 seconds.  Not in KMS mode. Note this benchmark runs in 10 seconds with jaunty on the same hardware.  karmic is 30% slower than jaunty.  According to the postings they're still working on the karmic ati driver....

Jerry

---

### Post by dros74 on 2009-08-15
> **dinxter said:**
> see [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/394985](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/394985)

thank you!!

fglrx loads with kermel 2.6.31-5, blacklisting drm, radeon and ttm and manually removing i915 as suggested on that bug report.
3d works!

---

### Post by jerrylamos on 2009-08-15
ati radeon Mobility 7500 IBM Thinkpad T40 working O.K. with karmic A4 drivers as on the CD.

Do note it is pig slow on video graphics benchmark GtkPerf available from Synaptic.  Jaunty runs the benchmark in 12.54 seconds while with radeon.modeset=1 the benchmark takes 40 seconds.  I think that's why radeon.modeset=1 is not default (yet).  With radeon.modeset=0 it takes 16.30  seconds which is "only" 30% slower....

Jerry

---

