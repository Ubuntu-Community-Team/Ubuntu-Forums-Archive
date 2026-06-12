---
title: "Problem getting graphics card working"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by DivineJustice on 2008-05-22
Sorry the title is a little vague

My computer got messed up when my cousin turned off during an upgrade and I had to reinstall Ubuntu. I had my monitor plugged into my Nvidia graphics card, but after the restart the card wouldn't work. I'm guessing that the driver isn't installed and that would make sense. I downloaded the driver from Nvidia, but it will not let me install. I currently have the monitor plugged directly into the motherboard, but it makes everything grainy and reading text is impossible. Also under hardware drivers it says NVIDIA accelerated graphics driver is not enabled, but whenever I enable and restart my computer gets screwed up and I have to reinstall


Nvidia GeForce FX 5200
Ubuntu 8.04

Does anyone know how to install the driver?

---

### Post by yochaigal on 2008-05-22
Firstly, you don't ever need to reinstall.


I've seen this problem before, it seems to be hardy-specific.
When you enable the restricted drivers, your display is messed up, or gnome won't login.  

Try this:

Download envy.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It will find the correct drivers for you and install them.

---

