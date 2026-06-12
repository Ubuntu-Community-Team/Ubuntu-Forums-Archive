---
title: "Unable to enable secondary monitor on ubuntu 14.04"
date: 2014-05-07
forum: Installation &amp; Upgrades
---

### Post by Davinellulinvega on 2014-05-07
Hello everybody,

Here is my problem:
I recently installed the latest version of ubuntu-gnome(14.04). I happily tried to watch a film on my video projector, but when I plugged the projector through the VGA port, nothing appears and the projector stays disabled.
Here is the result of the xrandr -q command:
```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 277mm x 156mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected (normal left inverted right x axis y axis)
   800x600        60.3 +  120.1     72.2     75.0     56.2  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1366x768       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1280x720      120.0     60.0  
   1024x768      120.0     75.1     70.1     60.0  
   832x624        74.6  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1 

```

And here are the details about the graphic card:
```
description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:6000(size=64)



```

Does anyone have any idea where could the problem come from?

**Edit: **After looking into the Xorg.log it seems that right after I try to enable the second display, there is a framebuffer resize that is automatically triggered. However, the size of the framebuffer is set to 1366x768, so the exact size of the primary display.
As I am no expert when it comes down to this, I ask you could this be a trail to solve the myster?

Thank you for the help you could provide.

---

### Post by Davinellulinvega on 2014-05-08
So here I am again answering to myself.

The problem wasn't from ubuntu or any other package, it was all due to my own stupidity. I forgot that I had a script running in background to automatically rotate the screen according to the position of the computer. And because in this script I only use the xrandr command on the LVDS1 display any other display will be disabled automatically. Hence the problem discribed.

---

