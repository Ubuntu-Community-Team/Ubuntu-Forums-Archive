---
title: "A couple of package installation errors"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by Sleaka J on 2008-02-22
Ok, I had 7.04 installed and I didn't have issues installing these packages under that, but I wiped that before installing 7.10.

When I try and install Wine, I get the following error message:
> 
wine:
 Depends: libaudio2  but it is not installable


When I try and use the Restricted Nvidia Driver, I get the following error message:
> 
The software source for the package

   nvidia-glx-new

 is not enabled.


Neither offer anything but a Close button. Now, I'm a bit of a noob when it comes to Linux, but I understand the gist of it, I managed to install X about 10 years ago (back before they had GUI installations), but it's been a while.

Hope someone can help me...

---

### Post by taurus on 2008-02-22
Do you have all your repos enable in /etc/apt/sources.list?  Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark in front of all the lines except the last one, Source code, and cdrom in the window below.  Close it and press Refresh.  Now, see if you can install anything from there.

---

### Post by Sleaka J on 2008-02-22
I checked my source list and checked the boxes you mentioned.

It fixed both of my issues. Wine downloaded fine after that and I was able to enable the Restricted Driver for my video card.

You just received another thanks.

---

