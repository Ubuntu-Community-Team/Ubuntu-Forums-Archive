---
title: "Ubuntu on my laptop"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by nomorevista_302 on 2008-04-18
I want to install ubuntu on my new laptop.

The cd boots, I select "start or install Ubuntu",  stuff loads, the ubuntu heading shows up with the loading bar  below it, then when thats done my computer tells me " Failed to start X server ( your graphical interface). It is most likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?". There it give me the choice of yes or no. After pressing "no" it returns to the ubuntu header and it tells me to remove the CD and press enter. 

PLease help me get away from vista:lolflag:

---

### Post by ibutho on 2008-04-18
Hi.

When you boot from the Ubuntu live disc, select the option for "safe graphics" and see if that helps.

---

### Post by odin1965 on 2008-04-18
Do you know what type of graphics you have? Nvidia, Intel, Ati? Also, make sure you are using a new version of Ubuntu, at least 7.10, there's better support for newer laptop graphics cards. You could try the 8.04 beta as well.

If nothing works, you may have to edit xorg.conf to use the VESA driver to get you started. It's not as hard as it sounds, we can help if you need to do that.

---

### Post by nomorevista_302 on 2008-04-18
> **odin1965 said:**
> Do you know what type of graphics you have? Nvidia, Intel, Ati? Also, make sure you are using a new version of Ubuntu, at least 7.10, there's better support for newer laptop graphics cards. You could try the 8.04 beta as well.

If nothing works, you may have to edit xorg.conf to use the VESA driver to get you started. It's not as hard as it sounds, we can help if you need to do that.

I got the same results with safe graphics mode. My laptop has Nvidia graphics. I have been trying to install 6.10, where can I find 7.10, or something better that might work?

---

### Post by pbcartwright on 2008-04-18
to download, go to ubuntu.com, find the download link..select a location.. or go here to pick which version you want:
[http://mirror.anl.gov/pub/ubuntu-iso/CDs/](http://mirror.anl.gov/pub/ubuntu-iso/CDs/)

for graphics you can either
1. edit /etc/X11/xorg.conf and change your display driver from nvidia to nv then it will work, though the nv driver isn't near as good as the nvidia. Once up in X you can download a package called envy, then let it configure your graphics card.
2. run this command:
sudo dpkg-reconfigure xserver-xorg

then select the nv or nvidia driver. to install nvidia you might also need the kernel headers installed..

do a google search for ubuntu +NVIDIA +configure

---

### Post by nomorevista_302 on 2008-04-18
> **nomorevista_302 said:**
> I got the same results with safe graphics mode. My laptop has Nvidia graphics. I have been trying to install 6.10, where can I find 7.10, or something better that might work?

ok, I got 7.10 downloading right now. If install fails again how do I  edit xorg.conf to use the VESA driver?

---

