---
title: "Login Resolution 1920x1200 on a 1600x1200 Screen"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by Kuntabunt on 2005-09-13
Hello,

i am realy new in Ubuntu and have only few experiance with other linux distributions. Furthermore, my english is not as god as it should be.
I hope you can help me anyway.

My monitor:
Fujitsu Siemens
TFT: 5110 FA
resolution up to: 1600x1200
Frequency: 60Hz
(on lower resolutions 75Hz)

During install the monitor would be corrct detected.
But the frequency seems to high, so the monitor turns off at the start of xorg.
After manual configuration of the xorg.conf (1600x1200 @ 60Hz) the loginmanager is displayed but the icons looks a little smal. 

The default configuration for the KDE is 1920x1200 after install on my system. I have changed it to 1600x1200 for the KDE but I can not find how to configure it for the login manager.

My monitor accept a miximal resolution of 1600x1200 but it shows the 1920x1200 resolution so xorg seems to make a rendering from the higher to the lower resolution.

I would be happy about any help

---

### Post by evilghost on 2005-09-13
Have you tried to modify /etc/X11/xorg.conf directly to make the resolution changes?

---

### Post by Kuntabunt on 2005-09-14
Yes I have changed the xorg.conf directly with an editor

---

