---
title: "After upgrade to 12.04 tv out switches to PAL"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by gkffjcs on 2012-05-26
Hey all, I did not know where I should put this, but the problem started after upgrading to ubuntu 12.04. 

I have an older system which had been running ubuntu 11.10. I have it attached to a television via S-Video on my video card. 

When I upgraded to 11.04 a year ago and re-booted the video out switched to pal mid-boot, I live in the U.S. and my television requires NTSC, at the time I did some research and managed to fix the problem by adding the line "options nouveau modeset=0" to the file /etc/modprobe.d/nouveau-kms.conf

This fixed the probelm in ubuntu 11.04 and agian in 11.10 however, it does not solve the problem in 12.04 after searching google I cannot find any reference to anyone having this probelm in 12.04, how do I prevent the output from my graphics card being switching to PAL during the boot process?

Note: this is NOT an X11 problem since it happens before x11 loads, and effects the console output aswell as any later instance of X11.

---

