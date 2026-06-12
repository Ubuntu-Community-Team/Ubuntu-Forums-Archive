---
title: "x11:can't get 1920x1200_60 to 'stick'"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by davidmaxwaterman on 2008-03-21
Hi,

I am attempting to get my display to be 1920x1200_60 which is the native resolution of my HP L2335. I have an Nvidia FX5200 and have the proprietary drivers installed.

The login screen is at the correct resolution (I can tell from the monitor's status panel), but when I log in, it resorts to 1280x960_85. Running 'sudo nvidia_settings' and selecting the 1920x1200_60 (again) and applying works, and I save the configuration to xorg.conf (without 'merge'), but ...logging out gives me the correct resolution for the login screen, but logging in again results in it going back to 1280x96_85.

Anyone any ideas?

Max.

PS. When it's how I want it to be, the monitor reports the 'Horz Freq' to be '74.82KHz' (vert is 60Hz and resolution is 1920x1200, as expected).

---

