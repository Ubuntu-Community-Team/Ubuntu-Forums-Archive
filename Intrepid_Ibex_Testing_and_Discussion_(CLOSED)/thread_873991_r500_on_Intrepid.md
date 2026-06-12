---
title: "r500 on Intrepid"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sastraxi on 2008-07-29
So, as far as I can tell, fglrx won't work with this release yet. Correct?

Then, my question is simple: how can I get the ati driver to work with 3D acceleration, EXA acceleration, and textured video? I have an X1400. It tells me this:


(EE) RADEON(0): [dri] RADEONDRIGetVersion failed because of a version mismatch.
[dri] radeon.o kernel module version is 8.51.3 but version 1.17.0 or newer is needed.
[dri] Disabling DRI.

Any clues?

---

### Post by psyke83 on 2008-07-29
> **Sastraxi said:**
> So, as far as I can tell, fglrx won't work with this release yet. Correct?

Then, my question is simple: how can I get the ati driver to work with 3D acceleration, EXA acceleration, and textured video? I have an X1400. It tells me this:


(EE) RADEON(0): [dri] RADEONDRIGetVersion failed because of a version mismatch.
[dri] radeon.o kernel module version is 8.51.3 but version 1.17.0 or newer is needed.
[dri] Disabling DRI.

Any clues?

Do you have any old fglrx packages installed? Supposedly they can conflict with the DRI drivers. Purge all fglrx packages and reinstall libgl1-mesa-dri and libgl1-mesa-glx, then reboot.

---

### Post by FunkyRider on 2008-09-30
Yes, by installing fglrx, you official fscked up every thing regards to DRM/DRI Xorg GLX and stuff. Try completely remove fglrx and re-install xf86-video-ati, or install OS

---

### Post by krazyd on 2008-10-01
> **Sastraxi said:**
> So, as far as I can tell, fglrx won't work with this release yet. Correct?

Then, my question is simple: how can I get the ati driver to work with 3D acceleration, EXA acceleration, and textured video? I have an X1400. It tells me this:


(EE) RADEON(0): [dri] RADEONDRIGetVersion failed because of a version mismatch.
[dri] radeon.o kernel module version is 8.51.3 but version 1.17.0 or newer is needed.
[dri] Disabling DRI.

Any clues?
As indicated above, a clean install is probably the best solution.

For video to work with 3d on r500 in the current ati driver you need to add ```
    Option "AccelMethod" "exa"
``` to the Device section of your xorg.conf

---

