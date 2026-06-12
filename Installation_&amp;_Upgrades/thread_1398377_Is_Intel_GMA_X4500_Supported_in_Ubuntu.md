---
title: "Is Intel GMA X4500 Supported in Ubuntu?"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by Luggy on 2010-02-04
Hi Everyone,

My computer just died and I'm looking to replace it.

I'm interested in the Asus P5G41-M LE that has an integrated Intel GMA X4500 graphics processor.

I want to know if that graphics processor is supported in Karmic and if it will run the basic desktop effects.

Thanks!

---

### Post by VCSkier on 2010-02-06
I too, am curious about this.  Generally, Intel is excellent at providing good open source drivers for their hardware right away, so I would assume that the X4500 would be supported.  On the other hand, I do know that all of the Intel xorg drivers were in a very poor state upon the release of 9.04.  Generally, things improved greatly by the time of the release of 9.10.  Therefore, I feel confident in assuming that at least by the time 10.04 rolls out, X4500 will be doing great.  Of course, this is all based on generalizations and assumptions.  If anyone has any real knowledge about this, please feel free to speak up.

---

### Post by David Valentine on 2010-02-09
This is just a bump to indicate that I'm interested as well for exactly the same reasons.  If I run across an answer, I'll post it here.  But so far, no joy.

---

### Post by tea for one on 2010-02-10
I am also interested in this topic and I have located this supplier in the UK where the website states "tested with Ubuntu"

I haven't purchased the PC yet because I still want to do a bit more research.


[http://www.very-pc.co.uk/?section=Home%20Users&category=GreenPC&system=tt32-h](http://www.very-pc.co.uk/?section=Home%20Users&category=GreenPC&system=tt32-h)

---

### Post by keypox on 2010-03-18
runs very well.

---

### Post by hansdown on 2010-03-18
> **keypox said:**
> runs very well.

I second this.

It works very well.

---

### Post by asif_1088119 on 2010-04-02
i dont think it runs smooth..

---

### Post by frogotronic on 2010-06-07
> **asif_1088119 said:**
> i dont think it runs smooth..

Are the drivers part of Xorg?  Or does one have to install a binary blob?

Thanks,
CH

---

### Post by wtc on 2010-07-09
Hi,

I've installed ASUS P5QPL-AM G41 yesterday (and CPU Q8400), mboard has the X4500. Works out of the box in Lucid (driver "intel" in xorg), Compiz effects enabled, 720p and 1080p run visualy smoothly although didn't check fps yet. CPU load while HD playing not more than 10%.

Cheers

---

### Post by wtc on 2010-07-10
wtc@wtc-desktop:~$ glxgears
4079 frames in 5.0 seconds
4216 frames in 5.0 seconds
4191 frames in 5.0 seconds
4275 frames in 5.0 seconds

so should be ok.

---

### Post by kiriath-arba on 2010-09-19
Short answer is that Intel GMA X4500 works fine with Lucid for my friend, although there was an initial issue that needed resolving for ASRock Motherboard G41M-VS3.

The problem: i915 driver causes segmentation fault.

The fix: in the BIOS > Advanced > Chipset Settings change the Share Memory size (of onboard VGA) from "AUTO" to "128MB".

After this, the i915 loads properly, and then Xorg discovers the correct driver (intel) for the i915. This works on Ubuntu 10.04.1 64-bit and Ubuntu 10.04.1 32-bit alternative.

Note that on Ubuntu 8.10 the "intel" xorg driver does not support the i915, so it refuses to load.

sam@ubuntu10:~$ lsmod | grep intel
...
intel_agp              24119  2 i915
agpgart                31724  2 drm,intel_agp

sam@ubuntu10:~$ lsmod | grep i915
i915                  285076  3
drm_kms_helper         29297  1 i915
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
intel_agp              24119  2 i915

sam@ubuntu10:~$ grep drv /var/log/Xorg.0.log
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so

The "vesa" driver does work without changing the BIOS.  However, as might be expected, the speeds are better with the "intel" Xorg driver - approx 4000fps (as far as I can recall).

---

### Post by rickyrockrat on 2010-09-21
That works for me with a G41M-GS.  The 256M option is the same as the auto option - gives segfault.  You have to use 128M in the bios. Seems kinda pathetic that the driver has a set memory size.

Thanks,kiriath-arba!

The previous fix was to add i915.modeset=0 to the command line via /etc/default/grub (GRUB_CMDLINE_LINUX_DEFAULT), then running update-grub to modify the /boot/grub/grub.cfg

That works with any BIOS setting AFAIK, but you don't get drm (i.e. accellerated graphics)

---

### Post by LK2H on 2010-09-21
yep it does.

---

### Post by rulet on 2010-09-23
And how about supporting satellite HDTV -- is there any problem?

---

### Post by olligobber on 2010-09-30
> **kiriath-arba said:**
> short answer is that intel gma x4500 works fine with lucid for my friend, although there was an initial issue that needed resolving for asrock motherboard g41m-vs3.
 
The problem: I915 driver causes segmentation fault.
 
The fix: In the bios > advanced > chipset settings change the share memory size (of onboard vga) from "auto" to "128mb".
 
After this, the i915 loads properly, and then xorg discovers the correct driver (intel) for the i915. This works on ubuntu 10.04.1 64-bit and ubuntu 10.04.1 32-bit alternative.
 
Note that on ubuntu 8.10 the "intel" xorg driver does not support the i915, so it refuses to load.
 
Sam@ubuntu10:~$ lsmod | grep intel
...
Intel_agp 24119 2 i915
agpgart 31724 2 drm,intel_agp
 
sam@ubuntu10:~$ lsmod | grep i915
i915 285076 3
drm_kms_helper 29297 1 i915
drm 162377 4 i915,drm_kms_helper
i2c_algo_bit 5028 1 i915
video 17375 1 i915
intel_agp 24119 2 i915
 
sam@ubuntu10:~$ grep drv /var/log/xorg.0.log
(ii) loading /usr/lib/xorg/modules/drivers/intel_drv.so
(ii) loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(ii) loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(ii) unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(ii) unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(ii) loading /usr/lib/xorg/modules/input/evdev_drv.so
 
the "vesa" driver does work without changing the bios. However, as might be expected, the speeds are better with the "intel" xorg driver - approx 4000fps (as far as i can recall).
 
thankyou it works so much better now!!!

---

