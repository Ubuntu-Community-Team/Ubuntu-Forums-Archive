---
title: "Install kickstart without monitor"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by send2_jpg on 2011-08-11
Hi,
I got some problem with kickstart installation.
Right now I can install the ubuntu with kickstart method, but the process required the monitor to be connected and turn on on the computer. I would like to do it without monitor attached and turn on.
I already add this parameter :
xconfig --hsync=31.5-37.9  --vsync=50.0-70.0 --depth=8 --resolution=800x600 --defaultdesktop=GNOME --startxonboot

hoping that I could bypass the monitor identification process. But it did not work. The installation still hung, and when I attached and turn on the monitor, it shows blank screen. I can tell the process is hung because when I use the normal kickstart installation with monitor turned on the installation finished successfully.
the --hsync=31.5-37.9  --vsync=50.0-70.0 parameter i copy paste from the xorg.conf on the same machine after I successfull installation (with monitor turn on)

is there any trick to do kickstart installation without monitor? and I need the GUI (GNOME) and kinda lazy to install xconfiguration manually :D

thank's in adavance

---

