---
title: "Constant stuck in boot after update"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by anbaldinger on 2011-09-15
Hello,

I made an Update today (several things, all suggested by automatic updates) and since then my ubuntu 11.04 always gets stuck during booting at "Checking battery state".
Now this has happened before, but it is slightly different this time.
Normally something like this happens when a new kernel is installed and I have to reinstall my NVIDIA driver.
But thats just not working this time, because I can´t even change to another console with ctrl+alt+F1 (or different ones).
So i booted a previous kernel with "delete-key" at startup and choosing in grub.
But not even one of my previous kernels can boot the x-server any more. That has never happened before.
At least with the previous kernels I can change to a console, but then I cannot access the internet (wlan not working) or mount my external hard drive to get the NVIDIA-driver.

Has something like that ever happened to someone and/or do you know what to do now?

Thanks for your effort in advance.

Greets, Andrew

[SOLVED]
I booted with the ubuntu 11.04-disc, copied the NVIDIA-driver to my home, then started with previous kernel, changed to console, installed driver, started current kernel - could change to console suddenly - installed NVIDIA-driver again and it worked.
Strange though, something like that never happened before.

---

