---
title: "Fglrx with widescreen not working after upgrade to feisty"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by scananza on 2007-04-22
Hi all,
I have a box with following graphic hw:
- ATI Radeon X1300 card
- Acer 16:9 AL1916W monitor
On edgy I used the fglrx driver that, with a custom Modeline in the xorg.conf, run smooth at 1440x900@75Hz resolution. After upgrading to feisty, even if xorg.conf isn't changed and all the required packages (ati drivers et al.) are present, the monitor doesn't work, it stays black and keeps to popup a "Unsupported input" error message. The system is then unusable since vesa driver doesn't seem to work at more than 640x480 resolution  and xorg's ati doesn't work at all.
By the way xorg log message claims that fglrx driver doesn't support resolution of 1440x900 (but, as I said, I used it in edgy, can it be possible?)
Does anyone know if fglrx got some form of involution with feisty?

thank you a lot.

---

