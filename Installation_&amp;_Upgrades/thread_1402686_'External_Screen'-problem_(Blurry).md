---
title: "'External Screen'-problem (Blurry)"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by GoldenUFO on 2010-02-09
Hello all.

First of all, I am quite new at Ubunbu, as I have just installed it for the first time, so be gentle ;)

My problem is as follows:

I have installed the drivers for my graphics-card (correctly I think), but when I plugs in my external Screen, i cant make it work the way I want to.
I can find the screen, and have them both on at the same time, but the I can only set it to the 4:3 formats, 1024x768 and lower, but my screen is a widescreen :mad:

When I select the 'laptop'-screen and turns it of, my external screen gets all blurry, and it is impossible to see anything on it, which I do not understand.

INFO:
$ lspci | grep VGA
$ 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

Samsung SyncMaster 940MW 19"


I hope someone can help my :p

Greatings from Steffen.

---

### Post by efflandt on 2010-02-09
It is apparently normal for X to default to a resolution that works on both displays, since it does that even with my Toshiba with more capable graphics, reverting to 1024x768 for both laptop screen and 1080p HDTV.

I just tried an old Compaq V2000 which has same video as yours using xorg-driver-fglrx package in Ubuntu 9.10, and it too came up in 1024x768.

lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

From xrandr, it appears that it is not capable of my 1080p or your native 1440x900.  Following is xrandr after I switched off laptop display (LVDS) and changed to an existing 1360x768 mode with ($ indicates system prompt):

```
$ xrandr --output LVDS --off

$ xrandr --output VGA-0 --mode 1360x768

$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1360 x 1360
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected (normal left inverted right x axis y axis)
   1280x768       60.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)
```Note that it shows "maximum 1360 x 1360", but I don't know if that is total pixels (RAM limitation?), or that it cannot go wider than 1360 (frequency limitation?).  See what xrandr shows for your system.

And see [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) to test if other resolutions work for your system.  1440 x 900 is less that 1360 x 1360, so if it is a RAM limitation, maybe you could find a mode that would work.  Otherwise if xrandr shows a 1360x768 mode, you might try that like I did above (it worked on a different native 1280x720 HDTV that did not even list that mode in its docs).

---

