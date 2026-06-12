---
title: "Unable to install Ubuntu on Sony Vaio Y2 - general problem with Intel HD graphics?"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by one_paulie on 2010-10-02
Hi all,

I have been attempting to install Ubuntu on my Sony Vaio Y-series (VPCY2) with Intel HD integrated graphics. Unfortunately, I have been unsuccessful in my attempts.

I have tried the following versions:

- Ubuntu 9.10 from CD and bootable USB
- Ubuntu 10.04 from CD and bootable USB
- Ubuntu 10.10 from bootable USB

All of these attempts have encountered a non-responsive black screen from the start, no splash screen, no menu, no option for live-cd use, nothing.

It seems to be a similar problem to that discussed here ([http://ubuntuforums.org/showthread.php?t=1550153&highlight=vpcy2](http://ubuntuforums.org/showthread.php?t=1550153&highlight=vpcy2)), but that hasn't come up with any solutions yet. I think it might have something to do with incompatibility with the intel integrated graphics - but if this is the case, I am surprised that even the latest Ubuntu 10.10 has the same problem.

Any help and/or guidance would be greatly appreciated, I've been trying this for a while now, and am on the point of giving up.

Many thanks,

Paul

---

### Post by spcwingo on 2010-10-03
Have you tried these kernel parameters at boot:

```
i915.modeset=0
```

or

```
i915.modeset=1
```

I've had laptops I've installed Ubuntu on that did exactly what you're describing.  If you need help with inputting those parameters just let me know.  ;)

---

### Post by thelastquincy on 2010-10-03
i have the same graphics card and I have no problems installing ubuntu. are u booting from a live cd? usb? i would check that you have a clean disk and the correct iso. :)

---

### Post by one_paulie on 2010-10-03
> **spcwingo said:**
> Have you tried these kernel parameters at boot:

```
i915.modeset=0
```

or

```
i915.modeset=1
```

I've had laptops I've installed Ubuntu on that did exactly what you're describing.  If you need help with inputting those parameters just let me know.  ;)

Thanks both for the replies :-) I did try both of these parameter settings - unfortunately the second one had no effect, and the first one did allow booting the live cd, but then everything conssitently freezes. I did only try this with 10.04 - do you think that it will make any difference if I try it with 10.10? I'm afraid that I tried this a little while ago and can't remember the details. I can try again in the next few days though with 9.10 and 10.10 from USB.

I have a live cd for both 9.10 and 10.04 which I've used to install Ubuntu successfully on other machines, but they don't work on the Sony laptop which is why I think its a hardware issue rather than a broken image. Now I'm using USB installs just because its easier - reformatting the USB drive each time. 

My intention is to dual boot windows 7 (required for work, already installed) with Ubuntu (also required for work, but also personal stuff), so I can't go from an empty hard disk (if that's what you meant).

Thanks again.

---

### Post by etrams on 2010-10-04
You need to download the alternative installer and install in text-based. Once you have installed you need to add "nomodeset" to your kernel parameters. (press e to edit and just added after 'quiet splash'

That should take you to console, just login and run 

sudo Xorg -configure

that should create an xorg.conf file in /etc/X11/

Then edit that file and change the driver from intel to vesa.

Very likely you wont be able to change your resolution, but hey, it works!

---

### Post by tino.truppel on 2010-10-16
Hi,

I have the same issue with my Sony Vaio VPCY2, Intel HD Graphics and a fresh installed Ubuntu 10.10. After GRUB the internal screen goes black (back light is still on). However, an external monitor works.

I tried i915.modeset=0 and i915.modeset=1. Sure the VESA mode works, but VESA only supports 1024x768 and 800x600 (unusable with a widscreen).

I know other users with a VPCY2 and a ATI card do not have the problem.

Any help would be great. Even a hint where I can ask for help.

Thanks
Tino

---

### Post by xalbert76 on 2010-11-09
Did someone  manage to solve this issue ? I have the same problem on VPCY2 under Ubuntu 10.04. VESA works but with intel driver I must use the external screen. I noticed that xrandr gives the physical size next to LVDS1 as 0mm x 0mm. Does it mean the driver does not recognize the size of the laptop screen ? Could this point to a solution ?

Thanks,

Roman

---

### Post by spcwingo on 2010-11-09
Try:

```
nomodeset
```

---

