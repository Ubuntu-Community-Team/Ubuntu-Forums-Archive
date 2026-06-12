---
title: "Cannot boot i386 kernel, generic kernel doesn't like nvidia"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by bilbravo on 2007-04-20
I was running 6.10 on my Core2Duo, but using the x86 release due to Flash/Java.

I upgraded last night, and it took most of the night to do the download.  I woke up this morning and eagerly rebooted, and was greeted with the "Ubuntu" flash screen but the status bar doesn't move.  So I hit Alt + F1 and see "Loading..." and it sits for about 10 minutes while I take a shower.  Come back, same thing.

So I reboot, and select the "-generic" kernel in GRUB.  It boots up, but I get thrown back to the X.org error app/ASCII art display, saying X server could not start.  Not surprisingly, it was due to the "nvidia" module not being able to be loaded. So I modify /etc/X11/xorg.conf and change the driver to "nv" and commented out the "glx" line in the first section of xorg.conf.  Now, I notice that the upgrade changed my identifier string from "Default NVIDIA blah balh" to "Geforce 7600" (which is correct).

Reboot, same thing.

Any ideas what I can do to get in to X?  At that point I'm sure I can just get back in and re-install the drivers, but I'm a little confused by "nv" didn't work.

Edit:  Thought I'd add a little something, I can go either way with this--getting the i386 kernel to boot, or getting into X with the generic kernel.  However, I think that getting the i386 kernel to boot will likely end in the same result, X crashing out due to the nvidia driver.

---

### Post by elmerfud on 2007-04-20
Try:
$ sudo apt-get install nvidia-glx-new
$ sudo nvidia-glx-config enable

After that, check that xorg.conf is using "nvidia"

---

### Post by bilbravo on 2007-04-20
> **elmerfud said:**
> Try:
$ sudo apt-get install nvidia-glx-new
$ sudo nvidia-glx-config enable

After that, check that xorg.conf is using "nvidia"

I will try this when I get back to that machine, and update this thread accordingly.

Thank you for the suggestion.

---

