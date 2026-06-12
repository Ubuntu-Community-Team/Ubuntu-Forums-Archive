---
title: "Installation/GUI Error"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by White-Hat` on 2005-10-25
I have a problem. :(

I installed Ubuntu to one of my boxes and the installation went without error. I can boot to ubuntu in recovery mode just fine, without the GUI... But when I boot normally, it freezes and hangs at an underscore. This same problem happened with the live CD, as well as Kubuntu. Maybe it's my hardware? I'm not sure so any help is appreciated.

---

### Post by munkymonkjr on 2005-10-25
not sure waht you're saying here. but i'll try to get it straight. so you load it up and it all loads fine, then when X tries to come on, you get an underscore on the upper left and it just freezes, no error messages or anything?

first thing first try pressing Ctrl+Alt+Backspace to quit x. See if ubuntu isn't frozen PERIOD, and if at least you can get into text mode. Next, check virtual console 3 (alt+f3 i believe or maybe its just alt+3). it might show you the hardware. i'd try to reconfigure x (nano /etc/X11/xorg.conf) before i would say your hardware is to blame.

---

