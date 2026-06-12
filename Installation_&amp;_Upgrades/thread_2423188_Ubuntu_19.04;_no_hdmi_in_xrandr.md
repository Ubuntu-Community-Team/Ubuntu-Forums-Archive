---
title: "Ubuntu 19.04; no hdmi in xrandr"
date: 2019-07-18
forum: Installation &amp; Upgrades
---

### Post by spencer2 on 2019-07-18
I've done some upgrades over the last couple days & there is a persistent problem when my hdmi external monitor not working. I'd greatly appreciate some help please

xrandr output:

```
xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768      60.03*+
   1360x768      59.80    59.96  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 disconnected (normal left inverted right x axis y axis)


```

graphics card output:

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)


```

I've tried the gdm3 & lightdm switches but that hasn't worked either. When I go into my GUI update section: there is nothing listed in the additional drivers section: do I need to reload nvidia or something?

I ran "sudo ubuntu-drivers autoinstall" & got back 'no drivers found for installation'. Besides for a fresh install: what can I do please?

Surely there is a way to reload the HDMI option into xrandr or something.

---

