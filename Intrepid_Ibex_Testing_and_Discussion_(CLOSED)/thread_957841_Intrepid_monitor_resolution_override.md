---
title: "Intrepid monitor resolution override"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by RomeoJava on 2008-10-24
Hello everyone,

I'm really looking for some help. I'm running the Intrepid Beta which seems to be trying to be more intelligent about the resolutions my monitor supports than hardy, possibly due to Xorg changes. I've worked out that it is doing this by using EDID data from my monitor however my computer is in a rack and the monitor is attached via a 10 meter VGA cable which apparently prevents EDID from working. Therefore I need to find a way to force a higher resolution. I've tried adding a modeline to the xorg.conf without success and also I've tried the xrandr --newmode/--addmode without success as well. It is possible I've done one of these wrong but I'm really stuck. I have a feeling that this problem may also effect people with certain KVMs. I think users do need a reliable way to override the detection mechanisms. The bulletproof X 'improvements' have been less than helpful during the process too..

---

### Post by mr_fong on 2008-10-25
Same here. My Dell monitor is never detected, so I am used to correcting this in the config app of KDE or directly in xorg.conf. But in KDE4 there is no such place anymore (at least I can't find it) and xorg.conf is almost empty! Does this have something to do with HAL? --Hans

---

### Post by overdrank on 2008-10-25
Moved to  Intrepid Ibex Testing and Discussion :)

---

### Post by scandido on 2008-10-25
I am having a similar problem. I selected a resolution that was too high for my monitor, yet shown as available in the "Screen Resolution" control. Now I cannot get back into the GUI because it does not recognize that there is a problem, and keeps putting me into a resolution that cannot be displayed by my monitor. Unfortunately, there is little in the xorg.conf file besides "Configured Monitor", "Configured Video Card", etc.

Does anyone know of any way to make it forget its settings and go back to the installation defaults? I've tried the traditional 

sudo dpkg-reconfigure -phigh xserver-xorg

magic but it appears to generate another xorg.conf without many settings, and the resolution (not stored in xorg.conf) is still too high.

Thanks.

---

