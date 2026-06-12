---
title: "Mint 18 KDE: Suddenly no HDMI"
date: 2017-03-24
forum: MINT
---

### Post by accounts0 on 2017-03-24
Sometime overnight HDMI stopped working on my laptop, a Dell Inspiron 5559.

Upon reboot I found that it works right up until the point KDE loads, with it going out a few seconds after the "K with gear" circular progress indicator appears.

When I check KDE's "System Settings", only the laptop's built-in display is listed as an available option. But xrandr shows the HDMI-connected monitor.

There weren't any changes made AFAIK that could've prompted such an issue, but obviously something's gone wrong.

Ideas?

---

### Post by accounts0 on 2017-03-25
Here's what worked:
1) dist-upgrade, etc.
2) Upgraded kernel to latest 4.8 for good measure
3) Reboot
4) In KDE's "System Settings > Display and Monitor > [Select HDMI Device]", there's now an "Enable" checkbox I don't recall was there before. Upon checking that, I can now use HDMI as my "Primary display" there.

---

