---
title: "dual head output problem"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by naj342 on 2009-12-27
Hi,

I've found problem with using dual head capabilities of intel onboard video card. My mainboard is gigabyte GA-EG41MFT-US2H with popular x4500 intel video accelerator, it supports both hdmi and dvi-d connectors - but with standard 9.10 installation there are many blinking pixels (artifacts) visible on dvi-d connected display (only on dvi-d, nothing wrong happens with hdmi connected one). After several hours of fun (:/) I've found solution: creating xorg.conf with settings of color depth lowered to 16bit. 
But it sucks, does anybody found similar problem? - and maybe has some different solution? - I really would like to run my computer with 24bit color. Am I right the issue is xorg intel video driver?

best regards
naj342

---

