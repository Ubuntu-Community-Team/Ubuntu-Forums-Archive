---
title: "HDMI output is not working DVI1 I think"
date: 2012-10-15
forum: Installation &amp; Upgrades
---

### Post by Peter2009 on 2012-10-15
I am trying to connect a monitor to the HDMI video output but it is not working.

I have tested the monitor and its working but when I type on a terminal 

xrandr -q

I get:

```

Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 337mm x 270mm
   1280x1024      75.0*+   75.0*    60.0  
   1600x1024      60.2  
   1400x1050      60.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1360x768       60.0     59.8  
   1280x800       74.9     59.8  
   1152x864       75.0     75.0     70.0     60.0  
   1280x768       74.9     59.9  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        75.0     72.8     72.8     72.8     75.0     66.7     60.0     59.9     59.9  
   720x405        72.0  
   720x400        70.1  
LVDS1 connected 1280x800+1280+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)


``` 

I have tried a few things from different internet source but nothing work.

The work that has happen is I turn VGA off and then try to turn up DVI1 and it reboot the Xor and I have to log in back again. But nothing change. Please help!

P.D. I am using 10.04 2.6.32-38

---

### Post by Peter2009 on 2012-10-15
If I do 

xrandr --output DVI1 --mode 1360x768_59.80

I get:

```

xrandr: cannot find crtc for output DVI1

```

After I did manually add the mode by:

```

cvt 1360 768 59.8
xrandr --newmode "1360x768_59.80" 84.50 1360 1432 1568 1776 768 771 781 798 -hsync +vsync
 xrandr --addmode DVI1 1360x768_59.80
xrandr --output TV1 --off
xrandr --output DVI1 --mode 1360x768_59.80
xrandr: cannot find crtc for output DVI1

```

---

### Post by Peter2009 on 2012-10-15
More info:

if I connect the monitor on the VGA output its the following settings

```

Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      75.0*+   60.0 +
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     60.0  
   720x400        70.1  



```

---

