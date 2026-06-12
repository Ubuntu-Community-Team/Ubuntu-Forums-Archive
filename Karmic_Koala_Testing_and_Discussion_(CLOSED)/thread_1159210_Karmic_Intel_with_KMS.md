---
title: "Karmic Intel with KMS"
date: 2009-05-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by marijus on 2009-05-14
none of the options described in [https://wiki.ubuntu.com/X/KernelModeSetting]("https://wiki.ubuntu.com/X/KernelModeSetting") will really enable KMS on my system. maybe i'm missing something?
 
The only thing which does enable KMS for me is to add i915.modeset=1 to the grub boot options.

Kernel: 2.6.30-5

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

What i found out is: if compiz is enabled my kernel log will be flooded by this kind of error messages: 

ubuntu kernel: [  253.817551] [drm:drm_wait_vblank] *ERROR* failed to acquire vblank counter, -22

about 40 of them per second!

using the drm, intel and mesa packages from xorg-edgers ppa doesnt make a difference...

any suggestions, comments?
regards!

marijus

---

### Post by Starks on 2009-05-14
> i915.modeset=1

That's grub option shouldn't work.

That was a Fedora-centric option that only applied during the infancy of KMS.

---

### Post by portis on 2009-05-15
Add this line
i915 modeset=1
to /etc/initramfs-tools/modules
and 
sudo update-initramfs -u

---

### Post by marijus on 2009-05-15
> **portis said:**
> Add this line
i915 modeset=1
to /etc/initramfs-tools/modules
and 
sudo update-initramfs -u

serious... this doesnt work for me either... i dont get the entry KMS enabled (or something similar... dont remember exactly...) in xorg.log.

i do get this entry if adding i915.modeset=1 to th bootoptions... also after the kernel modules are loaded during bootup i can see the screen resolution change -> fonts are getting smaller.

well... what about the errors in kernel log?
do you also get them while using compiz?

regards!
marijus

---

