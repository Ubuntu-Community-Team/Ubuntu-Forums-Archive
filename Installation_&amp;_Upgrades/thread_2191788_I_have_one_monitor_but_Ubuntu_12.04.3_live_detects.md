---
title: "I have one monitor but Ubuntu 12.04.3 live detects 2 monitors"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by nef1312 on 2013-12-04
I am planning to install Ubuntu 12.04.3 on computer which currently has Mint 12 and Windows 7, with Mint 12 being replaced by Ubuntu 12.04.3.

In the live session, my computer sees an extra, phantom, monitor (i.e., the monitor does not exist as I have only one monitor plugged into my computer). xrandr refers to it as an "unknown" monitor. This unknown monitor superimposes itself over the correctly detected Samsung monitor, but in the upper left hand portion of the desktop, with the two panels seemingly combined into one but the system tray portion of the panel showing twice. I was able to shut off the extra, "unknown" monitor, using the gui version of xrandr. I am concerned, with this sort of bug, about actually  installing Ubuntu 12.04.3, most particularly because I shall, in due course, also need to install the Nvidia driver for the graphics card.

Should I be concerned? And, if so, is there a fix for this problem, assuming that it persists after the actual installation of Ubuntu 12.04.3? Also, would installing the Nvidia driver resolve the problem?

My hardware is homemade, an Intel I5 processor, 8 GiB's memory and Nvidia GTX 550 ti graphics card.

---

### Post by ibjsb4 on 2013-12-06
Why not give 13.10 a try and see if it will do any better.

---

### Post by efflandt on 2013-12-06
Does your i5 or motherboard have any integrated graphics. In other words does "lspci" (without quotes) in a terminal show more than one **VGA** or **3D** device.

I have never had any issues with 64-bit 12.04 on an older i5 (in my sig) with GTX 550 Ti seeing anything other than the only monitor connected (actually 32" 1080p HDTV currently connected DVI to HDMI, but didn't matter if connected straight HDMI or VGA). Original graphics on that Dell PC was GT 220 only.

For a newer i7 laptop that has both integrated Intel HD 4600 and Nvidia GTX 765M I installed 64-bit 13.10 because I heard that it had best support for using both the Intel video for low power consumption and Nvidia for faster 3D graphics. But for a desktop you likely do not even want to use integrated video.

---

### Post by nef1312 on 2013-12-11
My apology for not responding earlier. I did not see that anyone had responded, after a number of days.

I made the mistake of installing Ultimate Edition 3.5, which does not seem to like my computer but which did not see phantom monitors.

In answer to the various questions:

My motherboard has only one monitor.

I do not want to use 13.10 because I want to use a LTS version.

---

