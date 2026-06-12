---
title: "nvidia drivers and display problems,"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by sumsa on 2008-05-02
I just upgraded to 8.04, using the |you have an update, thing that appeard on the menu bar|, and now i have quite a few display problems. 
before i upgraded i had everything running 3d accelerated on 2 monitors. but now after the reboot im stuck at 800x600 and a cloned view on both monitors. the keyboard layout is wrong as well| 

when i start up. the ubuntu load screen, you know, the one with the progress bar, is at a nice resulution of 1600x1200, but as soon as xorg starts, hell breaks loose. and it tells me that im running in low resolution, when i press configure, and configures the monitors to their right names and the nvidia 6600 to the right one. it just |forgets| what i just enterd and says that it is wrong as well. 

Ive tryed to look at the forums, but dident find anything that helped me

Im quite stuck now, and am unable to find any configuration tools in the system menu that can help me. I also tryed to use synaptic to reinstall the nvidia drivers, and activate them. use ALSA drivers, even tryed to use ATI once.. but to no awail.. 

My question is.. Is it possible to revert the update ;questionmark; and get back my old configuration|

---

### Post by Pumalite on 2008-05-02
How many OS's do you have and who owns the boot loader?

---

### Post by sumsa on 2008-05-02
I only have ubuntu, i physically exchange the harddisk if i want to run windows

---

### Post by Pumalite on 2008-05-02
Your problems are not going to go away so easily. You have this:
[http://ubuntuforums.org/showthread.php?t=623058](http://ubuntuforums.org/showthread.php?t=623058)
And a reinstall.

---

### Post by ansicplusplus on 2008-05-02
Hy,
try ```
gksudo displayconfig-gtk
``` to get to the display configuration dialog gutsy used to have.
Yours, ansicplusplus

---

