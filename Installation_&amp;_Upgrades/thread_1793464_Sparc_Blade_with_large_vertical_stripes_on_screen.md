---
title: "Sparc Blade with large vertical stripes on screen"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by PeterSprague on 2011-06-29
Hi,

I've got 10.04 installed on my Blade 1000 workstation.  Installed 6.06 first and worked my way up as per other postings.  See attached cookbooks I wrote.

Framebuffer is Elite3D-lite, and I have done the afbinit install.  Using Xorg w/ Gnome and other windowing software to eliminate the possibility it is Gnome.  From what I understand, Ubuntu does not require a custom X11 conf file like OpenBSD. 

Current screen output shows large vertical stripes, where the stripes overlay on top of the GNOME desktop.  Inside the stripes are the prior boot screen output of Ubuntu 10.04. When the screen saver kicks in, the Gnome desktop disappears, but the blue 10.04 stays visible.  Mouse cursor moves across the screen, under each stripe as it goes.

My knowledge of framebuffers is limited.  Would this then imply that the framebuffer is not fully "refreshing"?

The screen does not provide full width even though the correct OpenBoot monitor configuration is set.

Haven't found any mention of this issue from other Ubuntu/Linuxes Sparc users.

Attached the X11 log.  Looking at the log, I suspect this will need a custom X11 config file.

 Any ideas how to troubleshoot or possibly fix this?

---

### Post by PeterSprague on 2011-07-09
Can anyone help me with this?

Work for a trails non-profit, and really need this workstation up for our GIS  and web mapping work.

Next idea to pursue is possibly kernel boot options.

Peter

---

