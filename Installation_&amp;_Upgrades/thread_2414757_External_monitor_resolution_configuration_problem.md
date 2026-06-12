---
title: "External monitor resolution configuration problem"
date: 2019-03-14
forum: Installation &amp; Upgrades
---

### Post by Gingalone on 2019-03-14
I have a brand new Dell XPS13 laptop with pre-installed Ubuntu 18.04. 
Question: the resolution of the 13" built-in monitor is 3840x2160 and I connected a larger 24" monitor with a lower resolution of 1920x1080. Both monitor works, but in the laptop screen everything is far too small to be understandable while the external 26" is OK. In Settings > Devices > Displays I changed the scale from 100% to 200% with the result that the laptop display was OK, perfectly readable, but the external one shows enormous windows, fonts etc. 
So, I discovered that it is not possible (through the Settings utility) to set two different scales for the built-it and the external display...
Digging for a few hours in the web I found some hints on the use of the command xrandr which (as it looks) can solve the problem but with many trial and error I got only errors with very strange and at times surprising arrangements of the two displays...
Any help welcome!

---

### Post by TheFu on 2019-03-14
Please post the output from xrandr. Please wrap it in "code tags"  so columns line up correctly and we can easily read it.

BTW, there is a related tool, **lxrandr**, which is much easier to use, for simple needs. I don't have any displays higher than 1920x1200, so I've not run into the specific issue you have.

---

### Post by Gingalone on 2019-03-15
Thank you TheFu, here the xrandr output: ```
xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
eDP-1 connected (normal left inverted right x axis y axis)
   3840x2160     60.00 +  59.98    48.03    59.97  
   3200x1800     59.96    59.94  
   2880x1620     59.96    59.97  
   2560x1600     59.99    59.97  
   2560x1440     59.99    59.99    59.96    59.95  
   2048x1536     60.00  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   2048x1152     59.99    59.98    59.90    59.91  
   1920x1200     59.88    59.95  
   1920x1080     60.01    59.97    59.96    59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
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
DP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080     60.00*+
   1600x1200     60.00  
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      60.00  
   1152x864      75.00  
   1280x720      60.00  
   1024x768      75.03    60.00  
   1024x576      59.97  
   832x624       74.55  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08  
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
```

---

### Post by TheFu on 2019-03-15
Which variant of Ubuntu are you using?  The DE? 

[https://wiki.gnome.org/HowDoI/HiDpi](https://wiki.gnome.org/HowDoI/HiDpi) says:
> In theory, it can vary from monitor to monitor on a multi-monitor system whether the conditions for hi-dpi scaling are met. Under X11, GNOME currently supports only a single, global scale factor. For Wayland, we have per-monitor scaling. 
So if you are using X11 for the display, it isn't possible with Gnome DE to have per-monitor scaling.  Wayland was removed as the default after 17.10, but it is still available.  If you don't need the flexibility of X11, especially the networked aspects, then Wayland is a viable option.

If you have 2 different video cards (1 per monitor), then running 2 different X11 servers is possible. Each can have different DPI settings, but copy/paste between them doesn't automatically work without help. Long ago, I worked in an environment with 3 video cards and it was a pain. Perhaps a clipboard manager, which is common today, would solve that?

I fear the best answer is to buy a new HiDPI 2nd monitor.

---

### Post by Gingalone on 2019-03-18
Thank you TheFu, my Gnome version is 3.28.2...
Maybe, for sake of ease, I should try to work with just one monitor...

---

### Post by TheFu on 2019-03-18
> **Gingalone said:**
> Thank you TheFu, my Gnome version is 3.28.2...
Maybe, for sake of ease, I should try to work with just one monitor...

Up to you.  I'd try Wayland and see if that can do what you want.  I know it doesn't work for me, but I use some very specific X11 capabilities. Most people don't.

Wayland should be installed already - access it on the login page, before you login, there should be a "gear" somewhere. Different DEs have that different places for it. Click it and choose something like "Gnome3 (Wayland)" ... or the one that doesn't say X11.  I don't actually know, since I don't use Gnome3 or 18.xx.

If Wayland isn't already installed, it shouldn't harm anything to install it.  If it isn't as an option under the "gear", I would assume it isn't installed.

X11 and Wayland are known as "display servers."  X11 is a client/server architecture designed to work over IP networks.  The fact that most people use it all on the same machine is part of the reason why Wayland was created.  If you don't have to go through a network layer, there are some huge performance possibilities.  OTOH, if you routinely use the networked aspects of X11, like me, then Wayland isn't quite there.  I worked as an X11 programmer for 5 yrs. Mostly old-timers use it for all it can do.

You can google any terms above that aren't clear for more data.

---

### Post by Gingalone on 2019-03-19
Thank you TheFu, I'll give it (Wayland) a try as I don't have particular networking display necessity.

---

