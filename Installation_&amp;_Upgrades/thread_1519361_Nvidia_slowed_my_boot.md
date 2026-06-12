---
title: "Nvidia slowed my boot?"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by goseph on 2010-06-28
The darndest thing,

A fresh install of Lucid x64 followed by updates/upgrades and reboot led to an impressively quick boot. I tried enabling proprietary Nvidia drivers to see if that improved things and the boot seems similar but hangs at the wallpaper for about 30 seconds being perfectly responsive except for the top/bottom panels not appearing. I removed the nvidia driver hoping to get back to the panels appearing almost as soon as the wallpaper but they are still as slow as ever. I am sure that the only thing I changed was the Nvidia drivers. Is there anything I can do to track down what is going on and maybe even sort it?

---

### Post by dino99 on 2010-06-28
nvidia-current need to be activated (system admin hardware driver)

you can install the latest packages from this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by goseph on 2010-06-28
Hi, I have done as you suggested and added that ppa and done all updates / upgrades and enabled the current Nvidia driver. This has made no difference, I am starting to think that I incorrectly pointed to Nvidia when diagnosing the problem, maybe this is some sort of regression in the normal updates that I don't remember doing.

It seems unlikely to be a graphics driver issue because the whole desktop and Nautilus are fully responsive and "zippy", the panels just don't arrive for nearly 30 seconds after teh desktop is fully loaded, and when they do they are buggy. Attached is a screenshot showing what happens if I increase their size. Where do I report this kind of bug? Ubuntu or Gnome?

---

### Post by goseph on 2010-06-28
As ever, thanks for your time :)

---

