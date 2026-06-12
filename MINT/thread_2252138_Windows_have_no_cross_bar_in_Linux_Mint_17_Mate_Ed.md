---
title: "Windows have no cross bar in Linux Mint 17 Mate Edition."
date: 2014-11-09
forum: MINT
---

### Post by Muhammad_Ahmad_Mujtaba on 2014-11-09
Hello, Whenever I open any Window eg Firefox it open in maxmised mode with no sign of cross, minus and plus sign for quitting, minimising and maximising respectively. I can't go back but there's a fix around using Alt key and moving the window and after wards signs appears and When I again maximise it icons disappear, something looks like go beyond resolution of my current 16:9 ratio on 1366:786 monitor screen.
Any help?

---

### Post by ajgreeny on 2014-11-09
Is your monitor setting actually showing  the resolution being 1366:786 or something different?  It sounds as if you might have a higher resolution that is too large to fully show on your monitor.

Use command **xrandr** in terminal to see what the display currently is, and all the other possible resolutions your graphic card can manage.
Here's what mine shows:-
```
~$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 32767 x 32767
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9 +   75.0* 
   1400x1050      59.9  
   1280x1024      60.0  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     66.0     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-11-12
> ~ $ xrandrScreen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)


this is what it shows, plus I went to Menu > Monitor settings and it shows 16:9, 1366*768 resolution.


Plus, Every time I open the program It opens in full-screen maximised mode which is quit annoying now.

---

