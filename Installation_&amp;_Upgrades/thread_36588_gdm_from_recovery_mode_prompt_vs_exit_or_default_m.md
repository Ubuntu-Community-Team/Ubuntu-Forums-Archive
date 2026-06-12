---
title: "gdm from recovery mode prompt vs exit or default mode boot"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by matthew on 2005-05-23
Here's the deal, if I boot ubuntu in default mode all seems fine until gdm starts and suddenly my monitor displays a warning that either the HorizSync or VertRefresh is too high. I modified /etc/X11/xorg.conf in the "Monitor" section to include ranges well within the monitor's specifications, but this still happens.

The weird thing is that I can boot in recovery mode and type "gdm" at the prompt and all is well with the world. Gnome runs beautifully. However, if at that same prompt after booting in recovery mode I type "exit" I have the same experience as if I just boot in default mode.

So, here's my question as I try to figure out what is going on and try to fix it:

What is the difference between running gdm from the prompt when booting in recovery mode versus simply typing "exit" and letting it try to boot that way or booting in default mode?

What loads/doesn't load differently?

How can I find out? Is/are there different config files of some sort being used when booting or running gdm these different ways?

---

