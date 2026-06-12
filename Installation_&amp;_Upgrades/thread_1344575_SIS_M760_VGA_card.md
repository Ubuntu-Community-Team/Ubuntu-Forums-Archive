---
title: "SIS M760 VGA card"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by stefanus6667 on 2009-12-03
I have that VGA and a notebook with 1280x800 screen. When I installed the 9.10, I had bad colors.
I created a xorg.conf:

Section "Device"
Identifier "Configured Video Device"
Driver "sis"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
  Identifier     "Default Screen"
  Device     "Configured Video Device"
  Monitor     "Configured Monitor"
  DefaultDepth 24
  SubSection     "Display"
    Depth 24
    Modes "1024x800" "800x600" "640x480" "1280x800" "1600x1200"
  EndSubSection
EndSection

When I turn on my computer or reboot that I have bad colors, and the picture in bigger than my screen.

I can do this problem. First Driver "vesa" -> save->restart X (I have only 800x600 with good colors) than Driver "sis" ->save->restart X (I have good colors but the picture is bigger than my screen) after System->Settings->Screen->(now 1280x800) I set this for example 1280x168 save and after set that 1280x800. And Everything is good, but I have to do every turn on or restart.

I hope this is understandable  Plesae help me.

---

