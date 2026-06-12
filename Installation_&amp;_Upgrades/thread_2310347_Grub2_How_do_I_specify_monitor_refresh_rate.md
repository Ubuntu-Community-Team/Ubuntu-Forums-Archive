---
title: "Grub2: How do I specify monitor refresh rate?"
date: 2016-01-18
forum: Installation &amp; Upgrades
---

### Post by cablemunkey on 2016-01-18
I have a monitor which is very fussy about refresh rates. It maxes out at 1024x768, and it will only accept 75Hz refresh rate at this resolution. The display modes are never picked up correctly as the monitor's EDID data is wrong, however I can use it fine once logged in as I have setup .xprofile to add a custom mode using xrandr. This means that I cannot login using the terminal, and I cannot see any of the boot process or splash screens (also can't use BIOS but isn't a problem in this case). I've tried using the GRUB_GFXMODE= line in /etc/default/grub but this seems only to set resolution and colour depth. Any ideas?

---

