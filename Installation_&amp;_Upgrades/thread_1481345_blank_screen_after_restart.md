---
title: "blank screen after restart"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by bernacki on 2010-05-12
So I tried to install ubuntu 10.04 on my 5 year old gateway laptop but the screen kept going blank when ubuntu was booting up. I was able to get to the menu screen and add "i915.modeset=1" after "quiet splash", which allowed ubuntu to load. I installed it on the hard drive successfully, but when I restarted the computer, it won't load again. I don't know how to fix this so I can run it from the hard drive.

---

### Post by utnubuuser on 2010-05-12
you can add that line to /etc/default/grub so it's remembered between boots.

In /etc/default/grub find:> GRUB_CMDLINE_LINUX="quiet splash"
and change it to:> GRUB_CMDLINE_LINUX="quiet splash i915.modeset=1"

or give it its own line:> GRUB_CMDLINE_LINUX="i915.modeset=1"
save, then > sudo update-grub


Better instructions here:> [https://wiki.ubuntu.com/X/KernelModeSetting]("https://wiki.ubuntu.com/X/KernelModeSetting")

---

### Post by bernacki on 2010-05-12
How exactly do I do that? I'm not that experienced with stuff like this. When I start the computer up it goes to the Ubuntu loading screen for a few seconds and then the screen just goes blank right away.

---

### Post by Catharsis on 2010-05-12
Even better instructions here :)
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

