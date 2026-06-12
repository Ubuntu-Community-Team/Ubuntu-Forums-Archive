---
title: "Get external monitor to work with Nvidia Quattro K2000M"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by Askel on 2012-10-31
I got a Dell M4600 with Nvidia Quattro K2000M graficscard. I'm trying to get the external monitor to work with the displayport. But it can't find it.

I did install the proprietay drives before, but then I installed bumblebee and now it doesn't show any drivers when I check in third part software. And the monitor is still black. Ubuntu doesn't even recognice what graficscard it is. It says "unknown"

Are there any advice on how to make it work. I've tried to google myself to an answer but I still havn't found anything

I don't know what I did install that made th**e **proprietay drivers disappear in the first place

---

### Post by Askel on 2012-11-01
An update:
Before I tried to install some experimental driver. But this didn't show up on the "Additional drivers" list.  So I reinstalled Ubuntu entirely.

When I started it up the first time, the experimental drives showed up under "Additional drivers". I activated them and rebooted the computer, but then they where gone again. 

I've tried this command:
cat /etc/X11/xorg.conf

wich get the result:
cat: /etc/X11/xorg.conf: Filen eller katalogen finns inte (the file or catalog doesn't exist)

I've used Synaptic to install several Nvidia drivers but these doesn't show up either. I've also installed Nvidia X Server settings. When I start it up I get the message: 
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

which tells me nothing.

I hope someone here knows how to help me.

---

