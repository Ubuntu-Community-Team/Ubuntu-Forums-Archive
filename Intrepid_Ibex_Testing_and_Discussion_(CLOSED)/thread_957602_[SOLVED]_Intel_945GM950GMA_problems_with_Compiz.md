---
title: "[SOLVED] Intel 945GM/950GMA problems with Compiz"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Junk_head on 2008-10-24
OK I have a little problem with my fresh install of intrepid. Right now I can't enable Desktop effects on my external/laptop monitor (one is off other is on(external)) Now I didnt have any problems before using the external montitor. Compiz and 3d were working great. After using the screen resolution app to configure to use the external and laptop monitors is when compiz stopped working. Now I have tried disconnecting the external to get compiz running just on the laptop, but now it's the same thing error Desktop Effects could not be enabled. A peculular thing was with the external monitor connected while trying to enable effects is that a window would pop saying searching for drivers. I checked synaptic to see if the xorg-intel (which i assume is the driver correct?) and it was installed. This has got me stumped.
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

``` From running compiz --replace on the terminal.
Card on my laptop is Intel 945GM which had no problems with previous installs.

P.S: Ignoring the desktop effects problems, this is probably the best version of ubuntu I have ever used. Thank You Dev Team and Community! :D

---

### Post by Junk_head on 2008-10-24
Awesome Ive got my Desktop effects running again: here's what to do for those who may encounter the same: reconfigure your xorg again
:```
sudo dpkg-reconfigure xserver-xorg
``` Log out and log back in and enable your effects. I believe it was probably the screen resolution app that may have meddled with my xorg. W/e it may have been Im pretty happy to have everything working.

---

