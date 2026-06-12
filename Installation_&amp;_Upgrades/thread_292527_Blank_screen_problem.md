---
title: "Blank screen problem"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by Monstroxus on 2006-11-03
Hi,

I would like to install Edgy or Dapper on an older pc at work (acer  veriton 3200) It uses an i752 graphic card. I read somewhere that it is basically the same as an i810. Anyway, first of all I had to install by typing live acpi=off (otherwise there was only a blank screen). Install went fine, could surf the net etc... -> ready, reboot -> usplash, login successfull... then... blank screen.:confused:  Only the light brown color background with a cursor. (I still can use control-alt-f2 etc. though) 

Tried the following:

sudo dpkg-reconfigure xserver-xorg (also tried with the nano editor: sudo nano /etc/X11/xorg.conf)

Played around with all possible settings, changed the horizontal and vertical monitor settings, exactly according to the monitor's specifications. Changed the drivers to i810, i740, vesa, nv... (seems only i810 works) changed the color depth to different settings, changed the resolution settings... but nothing helped.. ](*,) 

I think the problem lies in the rare i752 graphic card.

Anyone any suggestions?

Thank you!

---

### Post by dcstar on 2006-11-04
> **Monstroxus said:**
> Hi,

I would like to install Edgy or Dapper on an older pc at work (acer  veriton 3200)
......
I think the problem lies in the rare i752 graphic card.

Anyone any suggestions?

Thank you!

It may well be something else, you can verify this by installing another video card (and remove/disable the first one) and trying the VESA mode.

If it still has the same issue, then it probably isn't that first video card (but at least you will know for sure.....)

---

