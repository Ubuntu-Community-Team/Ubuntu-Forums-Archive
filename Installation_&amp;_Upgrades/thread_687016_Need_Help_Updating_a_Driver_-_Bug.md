---
title: "Need Help Updating a Driver - Bug"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by Orange Juice on 2008-02-03
I downloaded and booted to the Ubuntu CD.

I chose "Start or install Ubuntu".

Loading Linux Kernel.

Ubuntu Loading screen (With the orange progress bar thing) (It does this for a while, a few minutes at least)

Then all these vertical blue lines show up, and it says "Ubuntu is running in low-graphics mode".

At this point, I've googled to try and find a resolution. I think a bug report was made a few days ago about it, and it's been fixed, but I'm not sure how to fix it.

What would be the easiest way to go about fixing my problem? I have a Dell Inspiron 1100, currently installed with Windows XP, and it has an "Intel® 82845G graphics controller".

**Quote from the report I found:**

[quote="xserver starts but display is corrupt (i830M,845G)"]
Alex's issue is fixed in xserver-xorg-video-intel - 2:2.2.0+git20080107-1ubuntu2:

I have the same hardware as Alex (thinkpad r31) and I was experiencing the same issue. X was using the vesa driver (poorly: fwiw toggling screen expansion fn-f8 would make it usable at 800x600).

I updated today to xserver-xorg-video-intel 2:2.2.0+git20080107-1ubuntu1 and now X works correctly using the intel driver (didn't try i810 as intel was autodetected).

I can't tell if this is the same issue as Dirk so I haven't commented on the bug 14065 upstream.

Now X works fine (modulu exa as in #177492: I changed my xorg.conf to use XAA and now X works as well as it does on my Gentoo partition, and as well as it did in Gutsy).
[/quote]
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/114331](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/114331)

---

### Post by Orange Juice on 2008-02-04
Any help on how to install the updated Intel video drivers through the terminal would be appreciated. I'm completely new to Linux so I don't know how to do it. :confused:

---

