---
title: "Unable to get dual screen with Karmic and ATI Radeon X600"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mlsquad on 2009-10-07
When I go to System->Preferences->Display, uncheck Mirror Screens and then click Apply I am asked if it should save to the configuration file.  I select yes and I am then asked to log out and back in.  When I do that I still have mirrored screens.  My graphics card is as follows.  Any suggestions?  I am running a brand new install of Karmic with all the updates using Wubi.

$ lspci | grep Display
01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]

---

### Post by Acer3810T on 2009-10-09
I have the same problem with an Ati Radeon 4870 X2.

Edit:

Changing my xorg.conf to increase the resolution of the virtual display of the default screen to 4096x4096 allowed me to use non-mirrored screens.


...
SubSection "Display"
                Virtual 4096 4096
EndSubSection
...

---

### Post by mlsquad on 2009-10-09
Any idea on  how to expand that to xinerama?

---

### Post by Longinus00 on 2009-10-09
This bug has been in for awhile now.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/438715](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/438715)
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/433856](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/433856)

---

