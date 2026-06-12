---
title: "Second screen white after upgrade to 13.04"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by pwlodarczak on 2013-04-28
Hi there,
I have an ASRock with a BenQ DVI display as my primary display and a Panasonic HDMI projector as second display. After upgrading to 13.04 from 12.10 the second display is just white and the mouse a black "x". I can still right click and get a popup menu. I played around with the xorg.conf settings and got the projector to work, but then the primary display is white with an x as mouse pointer. Can anybody tell me how to get both displays working? The GPU is nVidia and I also tried through nvidia-settings config panel, no luck.
Thank you
Peter

---

### Post by pwlodarczak on 2013-04-29
I found the solution in an other post. Separate X screens isn't supported by this version, TwinView has to be used.

---

