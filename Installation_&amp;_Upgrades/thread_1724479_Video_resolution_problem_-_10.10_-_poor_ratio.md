---
title: "Video resolution problem - 10.10 - poor ratio"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by castalla on 2011-04-08
Running Win7 on TV VGA displays at 1440x900 at 16:9 ratio - perfect.

Ubuntu 10.10 only offers 3 resolutions all at 4:3 - so the desktop is stretched.

Any advice on how to fix this?

---

### Post by Dutch70 on 2011-04-08
Oh yeah... 10:10 is a poor ratio. ;) j/k

I really don't know much about it, but a quick google search for "TV VGA display resolutions ubuntu" brought up this...and much more.
[[COLOR="RoyalBlue"]http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html[/COLOR]]("http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html")

Also, I don't think 1440x900 is 16:9, pretty sure it's 16:10.

---

### Post by realzippy on 2011-04-08
Which graphics card/driver/monitor model do you use?

---

### Post by castalla on 2011-04-08
The graphics are Intel 945 express - the monitor is a LCD flatscreen TV - identified as Plain Tree.

---

### Post by castalla on 2011-04-08
Following the xrandr advice ....

I tried this

xrandr --output VGA --mode 1440×900 --rate 59.9

I used 59.9 because that's what xrandr reported - or rather 59.9* whatever the * means ?

It works - ratio looks acceptable.

All a bit of a bodge, really.

---

### Post by realzippy on 2011-04-08
*whatever the * means*

..it means:
this resolution you use in the moment.
Also try (instead of xrandr --output VGA --mode 1440×900 --rate 59.9) :

```
xrandr -s 1440x900
```

which should work also.If so,add this command to 
system=>settings=>startupapplications
and you should be done.

---

### Post by Dutch70 on 2011-04-08
Great, glad you got it worked out. 

Please mark the thread solved if you're satisfied. :)

---

### Post by castalla on 2011-04-08
Okay - ratio fixed .... but another issue!

The top of the screen is just too high - is there any way to force the vertical height of the desktop down a notch or two?

I can do this using the TV's menu but it doesn't stick.

---

### Post by realzippy on 2011-04-08
please post the output from 

```
xrandr
```

..and what is the exact monitor model?

---

### Post by Dutch70 on 2011-04-08
Are you sure it doesn't have something to do with 1440x900 actually being a 16:10 ratio?

---

### Post by castalla on 2011-04-12
here's the output - monitor is identified as a Plain Tree.  It is actually a Medion MD 30169 LCD TV


mint@mint ~ $ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0 +
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1024x768       75.1     70.1     60.0* 
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0 +
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)

I've tried xvidtune but it doesn't work - no change in values.

---

### Post by realzippy on 2011-04-12
Medion MD 30169 LCD TV has a native resolution
1680x1050,so we should try to get this working.
..why do you use 1440x900 in Windows?

if *xrandr -s 1440x900* worked for you,try
```
xrandr -s 1680x1050
```

---

### Post by castalla on 2011-04-12
Thanks!   I'll try the options you quote.

The windows 1440x900 is selected automatically when I run Win7 and the TV auto-adjusts.

---

### Post by castalla on 2011-04-12
Nope - that native resolution just reduces the screen to lines!!!

---

### Post by realzippy on 2011-04-12
You have 2 monitors connected.
..can you disconnect the other and try again or is it a laptop?
...does 1680x1050 work in Windows?

---

### Post by castalla on 2011-04-12
Yes - it's a laptop.


I'll try win later today.

Thanks

---

### Post by EriktheAwful on 2011-04-12
Go through your TV's menus and see if there's an on/off setting for "Overscan". It should be off if you're using your TV as a computer monitor. I discovered this a few days ago on my Insignia TV. Turning it off lets me run at 1920x1080 right to the edges of the screen.

---

### Post by castalla on 2011-04-12
Thanks  - but no overscan option in menu.

---

### Post by realzippy on 2011-04-13
Do you have a HDMI port on the laptop?

---

### Post by castalla on 2011-04-14
> **realzippy said:**
> Do you have a HDMI port on the laptop?

Sadly, no - just vga

---

