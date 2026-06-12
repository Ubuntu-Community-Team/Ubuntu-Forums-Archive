---
title: "How to add additional display resolutions"
date: 2014-05-09
forum: Installation &amp; Upgrades
---

### Post by K.Kong on 2014-05-09
I have installed Ubuntu 14 in virtual machines, one in Windows 8 Hyper-V and another in VirtualBox on another PC.

I let the installation run using all the defaults.  The one in Hyper-V comes with only one display resolution: 1152x864.  The one in VirtualBox comes with one display resolution: 640x480.  Both are unsuitable for my work.  I need 800x600 and occasionally 1024x768.

I tried cvt 800 700 and got the Modeline:

   "800x600_60.00"  38.2  800 832 912 1024 600 603 607 624 -hsync +vsync

(xrandr on both installations always give "Failed to get size of gamma for output default".  I ignored this message.)

After doing xrandr --newmode ... followed by --addmode , I get to see 800x600 in Display Settings.  However, when I tried to apply, on the Hyper-V one I get: The selected configuration for displays could not be applied. required virtual size does not fit available size: requested=(800x600), minimum=(1152,864), maximum=(1152,864).   (I get a similar message in the other VM but this time the limit is 640x480.)  I ran xrandr -q and it gives:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1152 x 864, maximum 1152 x 864
default connected primary 1152x864+0+0 0mm x 0mm
   1152x864          0.0
   800x600_60.00  59.9

What have I done wrong?  What is the problem with failed to get size of gamma?

How can I change my display resolution?

Thanks.

---

