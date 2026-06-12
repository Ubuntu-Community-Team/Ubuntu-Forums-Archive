---
title: "Drivers to be installed on Ubuntu"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by yatendragoel on 2011-07-22
I have installed Ubuntu 10.10 on my Lenovo L420 thinkpad.

Now like windows, Is there any requirement to install drivers for video and others?

Somebody told me that in Ubuntu there is no need but I think that atleast video drivers are required because whenver I maximize a window, it doesn't maximized smoothly.

Q1. What all drivers need to be installed? Where can I find them?

---

### Post by dino99 on 2011-07-22
at startup the hardware is detected then the related drivers are installed and used, that it.

but you can check which one is installed with: sudo synaptic

---

### Post by coffeecat on 2011-07-22
According to a quick google, your Lenovo laptop has Intel graphics. Is this correct? If so, the appropriate intel driver is already installed and in use. Only with nvidia and ATI graphics are there separate proprietary video drivers as an alternative to the default open-source ones.

Your non-smooth maximising of a window might not be a video driver issue. Can you explain what happens in more detail? When you move unmaximised windows around, do they move smoothly or do you get any lagging or tearing? Do you experience any other graphical issues or artifacts?

---

