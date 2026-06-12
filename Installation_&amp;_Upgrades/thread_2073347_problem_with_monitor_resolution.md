---
title: "problem with monitor resolution"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by netipot on 2012-10-19
I just upgraded from lubuntu 12.04 to 12.10. It was fast & easy & I like it very much so far. I have encountered one problem however with my external monitor. I have a T60 Thinkpad which I use with a docking station connected to a Samsung syncmaster 732n external monitor. When I first log in my screen looks like the blue desktop. If I change the wallpaper then it looks normal like the yellow desktop, but if I log out & log back in then I have the same problem again with the new wallpaper. Also if I am using the same wallpaper for my other desktops they all have the same problem with the resolution, but if I use different wallpapers on my other desktops those wallpapers are unaffected. If I change any of them to the same wallpaper as the 1st desktop then they have the same resolution problem.
I need resolution.

---

### Post by netipot on 2012-10-19
Well I tried the default resolution, 1024 x 768 and all is cleared up, accept the true resolution is 1280 x 1024.
I want resolution.
Pun intended.

---

### Post by AgenT on 2012-10-20
While I cannot be sure, it looks like you are using XFCE. XFCE has issues when it comes to external monitors. A few people have already complained in IRC about this (server freenode, channel #ubuntu). 

Good news is: I think everyone fixed their problem. While I cannot tell you how to fix it since I do not use XFCE, I do suggest you try using xrandr.

First, check what xrandr shows as possible resolutions for your monitors by typing the following in a terminal:
```
xrandr
```I believe the the resolution with a * is what xrandr assumes to be the default.

Then try using xrandr to set the correct monitor settings, including resolution. It will be something like:
```
xrandr --output <NAME_OF_MONITOR> --mode <RESOLUTION_HERE>
```So for example:
```
xrandr --output DP1 --mode 1920x1200
```

---

### Post by netipot on 2012-10-20
> **AgenT said:**
> While I cannot be sure, it looks like you are using XFCE. XFCE has issues when it comes to external monitors. A few people have already complained in IRC about this (server freenode, channel #ubuntu). 

Good news is: I think everyone fixed their problem. While I cannot tell you how to fix it since I do not use XFCE, I do suggest you try using xrandr.

First, check what xrandr shows as possible resolutions for your monitors by typing the following in a terminal:
```
xrandr
```I believe the the resolution with a * is what xrandr assumes to be the default.

Then try using xrandr to set the correct monitor settings, including resolution. It will be something like:
```
xrandr --output <NAME_OF_MONITOR> --mode <RESOLUTION_HERE>
```So for example:
```
xrandr --output DP1 --mode 1920x1200
```

Actually I'm using LXDE "lubuntu".
 Does this work in LXDE?
I ran this in terminal & got this

neti@fret:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1024x768       60.0*+   75.1     70.1  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x800       74.9     59.8  
   1152x864       75.0  
   1280x768       74.9     59.9  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1400x1050      60.0 +   50.0  
   1280x1024      59.9     60.0  
   1280x960       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        60.0     59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)
neti@fret:~$ xrandr --VGA-0 --mode 1280x1024
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --current
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy

Don't see a difference.
Ran "xrandr" again & got the same read.

---

### Post by netipot on 2012-10-21
I have an ATI Radeon X1300 graphics card on my T60 Thinkpad
I am using a docking station to hook up to the external Samsung monitor.
Ubuntu says the Radeon X1300 is fully supported.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by blabla12345 on 2012-11-03
Got the same problem, also with Lubuntu 12.10 on a Thinkpad T61 and an external Samsung monitor (I only use the external monitor, the monitor of the Thinkpad is switched off(see Screenshot). There seem to be two different Desktops, one on top of the other (see Screenshot) hiding parts of the other. 
Please help!

---

### Post by netipot on 2012-11-05
It looks as if the desktop is affected but not the panel like mine. My desktop is divided into 4 & yours looks like 2. Does it affect your other desktops? 
It might be a bug.

---

### Post by netipot on 2012-11-05
I just did an update & now I can't change my desktop, & all of them are the same as "desktop 1".

---

### Post by netipot on 2012-11-05
I spoke too soon. After doing a restart I can change my desktop & all my other desktops came back, but I still have that resolution problem.

---

### Post by blabla12345 on 2012-11-10
> **netipot said:**
> It looks as if the desktop is affected but not the panel like mine. My desktop is divided into 4 & yours looks like 2. Does it affect your other desktops? 
It might be a bug.
Yes, my panel isn't affected at all, only the desktop. I only use one desktop but if I choose to use more they all have the same problem. And yes, it gets divided in 2.

---

