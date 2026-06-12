---
title: "Ubuntu 8.04 radeon gdm has wrong resolution"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by ralf.messerer on 2008-06-12
Hi,
After upgrading my notebook (hp/compaq N800V, radeon mobility 7500, display 1400x1050) from gentoo to ubuntu 8.04 (new installation) I have problems with the resolution of the login screen. It's allways 1280x1024. 
If I log in to a gnome session I can change the resolution from 1280x1024 to 1400x1050.

The problem seems something todo with 
>> (II) RADEON(0): Output LVDS using initial mode 1280x800

xrandr -q shows following:
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1400 x 1200
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 305mm x 228mm
   1400x1050      56.1  
   1280x800       60.0* 
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)

xresprobe ati shows following:
id: 
res: 1400x1050
freq: 
disptype: lcd/lvds

Now my question. How do I change the default resolution ti 1400x1050 ?

Following does not work:
1) dpkg-reconfigure  xserver-xorg
2) i have added in to the Section "Screen" 
        DefaultDepth    24
        SubSection "Display"
                Modes           "1400x1050"
        EndSubSection

regards,

Ralf

---

