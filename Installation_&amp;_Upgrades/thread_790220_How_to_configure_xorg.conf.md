---
title: "How to configure xorg.conf ?"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by woopud on 2008-05-11
Just installed 8.04 on my PC but have a problem with the screen resolution, the max I can get is 1024x800, I tried editing etc/X11/xorg.conf but there's nothing there to add possible screen resolutions ?

Bert

---

### Post by PmDematagoda on 2008-05-11
What is the VGA card you have?

---

### Post by woopud on 2008-05-11
It's A ATI Rage Pro XL

Bert

---

### Post by Gathalimay on 2008-05-11
I'm actually having the exact same problem and it is very frustrating. I installed nvidia-settings and I can set my resolution to the 1280x960 resolution I want, but I have to do this every time I boot up. there is an option to merge to the xorg file, but I also can't use "sudo" to run any programs, which is really really annoying (and is probably why it fails to merge with xorg, because it isn't using the root privelages). I can't sudo kate /etc/X11/xorg.conf because sudo doesn't work like that. . .I can still run kate by typing kate in the terminal, though.

Any help appreciated.

---

