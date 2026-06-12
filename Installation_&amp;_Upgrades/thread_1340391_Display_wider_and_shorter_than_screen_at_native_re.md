---
title: "Display wider and shorter than screen at native resolution on HP Pavilion"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by zzantozz on 2009-11-28
I got an HP p6243w-b (aka s5213w-b but with a 20" monitor) at Walmart yesterday. The monitor's native res is 1600x900, and Ubuntu seems to correctly detect and use that, but when it gets to the desktop, the image is stretched too wide and squashed too short. Specifically, the left side of the image is about an inch beyond the left of the monitor, the right side of the image is about three inches beyond the right of the monitor, and the top of the image is about an inch inside of the top of the monitor. The bottom of the image is in the right place. Something like this, where '*' is the monitor shape, and '-'/'|' is the desktop shape:
```
  ********************
|-*------------------*---|
| *                  *   |
| *                  *   |
| *                  *   |
|-********************---|
```

This same thing happens with either LiveCD or a straight install with all of the following (what I had on-hand):
9.10 amd64
9.10 i386
8.04 i386

Windows 7, provided with the computer, works just fine. Any suggestions?

---

