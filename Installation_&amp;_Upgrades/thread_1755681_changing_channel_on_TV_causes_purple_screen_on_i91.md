---
title: "changing channel on TV causes purple screen on i915  ubuntu"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by tuppe666 on 2011-05-11
I use my computer on a TV using a DVI to HDMI cable using an i915. Its been solid every release until this one. I change channel and then return to Ubuntu I get no signal/ Purple screen. I have tried turning off sync to vblank in compiz and running Gnome Desktop with no effects both seem to make no difference.

---

### Post by MAFoElffen on 2011-05-11
> **tuppe666 said:**
> I use my computer on a TV using a DVI to HDMI cable using an i915. Its been solid every release until this one. I change channel and then return to Ubuntu I get no signal/ Purple screen. I have tried turning off sync to vblank in compiz and running Gnome Desktop with no effects both seem to make no difference.
The graphics differences in this version is that the modes are set at default to auto (GFXMODE=auto) instead of in the past where the graphics mode was just set by the graphics drivers in a known mode for that specific hardware.

If you change channel on your monitor or disconnect the cable... it now, is going to search for a mode and is likely locking on an invalid mode causing your black screen.

If you "Set" your graphics hardware to a set resolution, then your hardware will stay in that resolution (and not look for others). 

You can do this in your system settings, editting the GFXMODE line of the /stc/defualt/grub..

DO NOT USE the startup-manager application with this chipset.  It adds a vga=xxx switch to the kernel boot line to set modes, which there is a known bug connected with this chipset, that using that switch to set modes will cause a black screen with this chipset.

---

