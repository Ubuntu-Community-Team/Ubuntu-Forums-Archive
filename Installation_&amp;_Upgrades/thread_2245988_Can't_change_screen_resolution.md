---
title: "Can't change screen resolution"
date: 2014-09-27
forum: Installation &amp; Upgrades
---

### Post by penguinboy561 on 2014-09-27
I'm having two issues with my Ubuntu 14 install, one I've band-aided, the other of which is making me pull my hair out.

1. I managed to install Ubuntu 14, but I get a black screen on boot, and my Acer monitor gives me the 'ol "Input not supported." I'm connecting using HDMI. I managed to get around this by using nomodeset. I don't know how to make nomodeset permanent, so I've had to reenter it on every boot. This is an annoyance, but here's the bigger problem:

2. I can't change the screen resolution. My monitor supports 1920x1080 resolution, but Ubuntu is defaulting to a paltry 1024x768 4:3, which looks atrocious and stretched out. It doesn't give me the option of changing it. I've tried downloading the latest nvidia drivers (my card in a GeForce GT 730), but that resulted in total failure and finally I had to reinstall Ubuntu. I've messed around a bit with xrandr, but nothing seems to be working.

I've heard that Ubuntu has issues with Acer monitors. unfortunately I don't have another one to test with and I'm not keen on buying one. Does anyone have any ideas to help this noob?

---

### Post by ajgreeny on 2014-09-27
> **penguinboy561 said:**
>  I've tried downloading the latest nvidia drivers (my card in a GeForce  GT 730), but that resulted in total failure and finally I had to  reinstall Ubuntu.
How did you do that?
You should use the "Additional Drivers" utility from dash, not go to nvidia direct, if that is what you did.

---

### Post by redrumrogue on 2014-09-27
I had a similar problem after installing Ubuntu Gnome 14.04 and found  that I had to set the desktop interface scaling to a value of 1.  I'm not sure that this is relevant to you with a unity ubuntu install but it's worth checking anyway.  To do  this type the following in terminal ... (as current user, not root)

** gsettings set org.gnome.desktop.interface scaling-factor 1**

You will need to reboot as well for the change to take full effect.

You can set this property through dconf-editor GUI as well.

Hope it helps!

---

