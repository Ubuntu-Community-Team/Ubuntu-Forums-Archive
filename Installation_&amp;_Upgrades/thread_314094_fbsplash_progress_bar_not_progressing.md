---
title: "fbsplash progress bar not progressing"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by ehula on 2006-12-07
I am running edgy with a custom 2.6.19-beyond1 kernel and have installed knn's Ubuntu fbsplash theme. Fbsplash displays on boot, but the progress bar stays at 0% and the message stays at "Initializing the kernel..." until the GDM login screen is displayed. The strange thing is that I use "suspend2ui_fbsplash" with suspend2, and the progress bar updates and the corresponding messages change properly. I have uninstalled "usplash" and I have run "update-initramfs -u".

Also, I am unable to see my text consoles (1-6) -- just black screens.

Any thoughts?

---

### Post by ehula on 2006-12-11
Solved...

I had to reconfigure the kernel. Some items were loading as modules.

---

