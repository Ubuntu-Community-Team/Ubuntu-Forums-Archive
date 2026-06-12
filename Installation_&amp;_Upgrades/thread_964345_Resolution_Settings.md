---
title: "Resolution Settings"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by jla on 2008-10-30
If I change the resolution settings with Monitor and Display System Settings.After I reboot they revert to their former settings.I'm using Kubuntu alternate cd 8.04.HP computer with Nvidia GeForce 6150 Se nforce 430 graphics built into motherboard.
   How do I prevent them from reverting back after each reboot.I'm using vesa driver.

---

### Post by martrn on 2008-10-30
Firstly make sure you have a valid  /etc/X11/xorg.conf  file.  Your /etc/X11/ xorg.conf should contain the correct setting to know valid X11 format for XORG.  One setup by failsafeX doesn't always work.  You can type 
```
sudo kate /etc/X11/xorg.conf
```
to edit or make changes to your xorg.conf  file.  Make sure there are no scrabled parts and its not empty.

Secondly  make sure you use the Nvidia  drivers or nv drivers not the vessa ones.  Use ```
http://albertomilone.com/envyngfaq.html
```  to install the nvidia binary drivers or just use the nv ones.

I presume you you have a invalid /etc/X11/xorg.conf file or one created by failsafeX. It will not work until you have a valid one.

If you are using GDM as your display manager you could
```
sudo apt-get install KDM
sudo apt-get remove --purge GDM
```
 to install the KDE desktop manager.  This will not give you a valid /etc/X11/xorg.conf  and on a reboot will not reset your display with low resoulution screen but instead will chuck you at the command line prompt.  

You really need a valid /etc/X11/xorg.conf so just copy one from someone who has the same monitor / graphics card you have.

---

### Post by jla on 2008-10-31
See reply below.

---

### Post by jla on 2008-10-31
Finally figured out how to fix this. Go to system setting>Monitor & Display>Administrator mode. Click the button to configure the video card and change it from plug n play to my actual card.(GeForce 6150 series). Then do the same for the monitor. Change it from generic to your actual one. (Delta 770 DC series). Then apply the changes, with the button and it regenerates a new xorg.conf with all the right new correct settings.

---

