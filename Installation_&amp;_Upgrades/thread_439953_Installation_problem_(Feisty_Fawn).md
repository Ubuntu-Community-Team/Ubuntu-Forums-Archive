---
title: "Installation problem (Feisty Fawn)"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by Xaimas on 2007-05-11
I installed Ubuntu 7.04 FF on my laptop fine, it had no problems and it runs like a dream. But when i tried installing it on my PC it's a different story, on my PC i have a NVIDIA GeForce 6800 GS Graphics Card with a ADC PnP Monitor with 1280×1024 - 32 Resolution.

When i booted Ubuntu from the Disk i used on my Laptop i put in my resolution but when it started up the Boot logo was not central, i thought nothing of it at first but when it went to the Desktop it was really weird, the icons and the menu bar were scattered everywhere and the mouse pointer was not visible, i tried with the other resoultions but was greeted with the same effect.

PLEASE HELP!!

---

### Post by hal8000 on 2007-05-11
Whenever I install Ubuntu (from 5.04 up to 7.04 inclusive) I always find that my monitor is probed and the graphics resolution is set to the maximum res of the monitor in my case 1600x1200. In my case this is too high so i always set things manually.

In your case I believe the same as happened, but either the graphics card cant match the monitors resolution or vice versa.
Two solutions:
ctrl-alt-f1
login as normal then
sudo dpkg-reconfigure xserver-xorg

(If an error message pops up complaining you are already running an X session then delete /tmp/.X0-lock )

The alternative is to use the utility under gnome system preferences to change resolution, but as you cant see the screen, this advice is less helpful.

---

### Post by Xaimas on 2007-05-11
Well it worked....

Sort of, all of it is fine except the mouse pointer, thats still invisible, any suggestions?

---

### Post by Xaimas on 2007-05-11
Any more suggestions people?

---

