---
title: "Monitor resolution crashed"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by Wer Bn on 2012-10-23
Hey guys

Today I switched on my computer and suddenly the resolution was of 640x480

[IMG]http://i.imgur.com/Xllo3.png[/IMG]

That message showed up.
Basically it says
"None of the chosen modes was compatible"
 
Now I can't change it.

Tried to opne Nvivida X server and it has no options.
It only says to put "sudo nvidia-xconfig" in terminal.
I did, and rebooted the PC. No changes.

What now?
Pleas help

Thanks

---

### Post by dino99 on 2012-10-23
what im seeing on the screenshot: CRTC

so you might need to try without xorg.conf (so dont use xconfig, its outdated nowadays) as the kernel directly deal with X

sudo rm /etc/X11/xorg.conf

then reboot

note: you did not said which nvidia driver is installed on which card. Be sure to use the good one, and if that fail, purge nvidia and use nouveau

---

### Post by Wer Bn on 2012-10-24
I have a NVidia 7600 GT

Which is the best driver?
The one selected in "Adicional Drivers" in "System Definitions" is "current version (recommended)"

Threre's also "version 173", "version 173-updates", "version current updates and experimental -304"

Which do I choose?

---

