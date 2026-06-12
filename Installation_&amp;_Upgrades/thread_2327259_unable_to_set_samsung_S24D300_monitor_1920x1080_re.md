---
title: "unable to set samsung S24D300 monitor 1920x1080 resolution"
date: 2016-06-09
forum: Installation &amp; Upgrades
---

### Post by Raymond_Tan on 2016-06-09
Hi,

I just bought a new second hand Samsung S24D300 monitor. According the the spec, the recommended resolution is 1920x1080. I share this monitor with my WIN10 laptop and the Font is sharp. However when I connect to my raspberry Pi 3 using Ubuntu MATE 16.04, the font is so blur. So i checked the monitor resolution using xrandr command, it show me that my resolution is 1824 x 984. No wonder my font is blur

 ```
raymond@raymond-desktop:~/debug$ xrandr 
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1824 x 984, current 1824 x 984, maximum 1920 x 1080
default connected primary 1824x984+0+0 0mm x 0mm
   1824x984       0.00*
``` 

So, I try to find some information from this forum from previous user got the same issue. They managed to solve it and I follow their solution as advise in this forum. Unfortunately, I still could not solve this issue. Please advise me what to do?

Many Thanks,
Raymond Tan

```
raymond@raymond-desktop:/etc$ man cvt
raymond@raymond-desktop:/etc$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
```

```
raymond@raymond-desktop:/etc$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1824 x 984, current 1824 x 984, maximum 1824 x 984
default connected primary 1824x984+0+0 0mm x 0mm
   1824x984       0.00*
```

```
raymond@raymond-desktop:/etc$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr: Failed to get size of gamma for output default
```

```
raymond@raymond-desktop:/etc$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1824 x 984, current 1824 x 984, maximum 1824 x 984
default connected primary 1824x984+0+0 0mm x 0mm
   1824x984       0.00*
  1920x1080_60.00 (0x2f8) 173.000MHz -HSync +VSync
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock  67.16KHz
        v: height 1080 start 1083 end 1088 total 1120           clock  59.96Hz
```

```
raymond@raymond-desktop:/etc$ xrandr --addmode default 1920x1080_60.00
xrandr: Failed to get size of gamma for output default
```

```
raymond@raymond-desktop:/etc$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1824 x 984, current 1824 x 984, maximum 1920 x 1080
default connected primary 1824x984+0+0 0mm x 0mm
   1824x984       0.00*
   1920x1080_60.00  59.96
```

```
raymond@raymond-desktop:/etc$ xrandr --output default --mode 1920x1080_60.00
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
```

```
raymond@raymond-desktop:/etc$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1824 x 984, current 1824 x 984, maximum 1920 x 1080
default connected primary 1824x984+0+0 0mm x 0mm
   1824x984       0.00*
   1920x1080_60.00  59.96
```

---

### Post by Raymond_Tan on 2016-06-09
Hi,

I just messed up the /usr/share/X11/xorg.conf file, now it just hang during intialise the X11 GUI? After the bios boot up, anybody know how to get into the command line so that I can sudo and copy the default xorg.conf back? It is so silly of me, I suppose to set the Ubuntu to command line after booting, then use startx to goto GUI. 

Many Thanks,
Raymond

---

### Post by X-RED_Tech on 2016-06-09
Raspeberry Pi3 has HDMI output only, right? And your monitor has VGA and DVI... So, you must be using some adapter.
HDMI-DVI requires a simple adapter as they're both digital and it should work exactly as a direct HDMI.
HDMI-VGA requires a converter and the maximum resolution is dictated by that and not the monitor itself.

---

### Post by Raymond_Tan on 2016-06-09
Hi X-RED_Tech,

Thank you for your reply. The Samsumg S24D300 come with HDMI connection. So, I connected my Raspberry Pi3 using HDMI connection to Samsung Monitor. I think the Raspberry Pi3 video driver unable  support 1920x1080 resolution, so I manually force is using 1920x1080 and ended up it hang during X11 initialization stage. 

Phew, A last I managed to login in the command mode and copied back the Xorg.conf. 

Many Thanks,
Raymond

---

### Post by X-RED_Tech on 2016-06-09
I would try 720P, the recommended resolution for Ubuntu running in other similar ARM devices.
I was able to run FHD in a Rockchip miniPC not much different but comes with Android. I no longer have it and there was a huge problem with a certain update - Ubuntu running from the external microSD - that broke the video.

---

### Post by QIII on 2016-06-09
Where is the previous forum thread?  It's tough for us to help when we have no idea what you did.

What recent changes did you do to xorg.conf?  Again, we can't advise without details.

---

### Post by Raymond_Tan on 2016-06-10
Dear X-RED_Tech,

Last few years back, I bought the 2nd release of Raspberry Pi B model which only have single core of 700Mhz with 512M Ram. I had try it using Raspian and quite impressed with it performance but due to 512Mbyte Ram, it cannot replace my desktop. With the new Raspberry Pi3 of Quad core of 1.2Ghz with 1G Ram, I thought to try it again with ubuntu to replace my desktop, but the font in firefox is not as sharp as window 10. I think this is because the video core in Raspberry Pi 3 cannot support 1920x1080 resolution. The main intention of Raspberry pi3 is use for cheap hardware for coding class and I'm think they achieve what it suppose to do. I will use the raspberry pi for headless computer for my coding. Hopefully one day, the Raspberry Pi foundation will release another more powerful Small Board Computer that can replace the desktop.

Cheers,
Raymond

---

### Post by Raymond_Tan on 2016-06-10
Dear QIII,

Basically, I read up the x11 manual and create the Monitor and Screen section in xorg.conf. After I reboot the Rapberry Pi3, the bios initialization looks fine to me but when it try to initiliase the X11 GUI, it complaint about 1920x1080 resolution not supported. Then It just hang there...From the pop-up window message,then I only noticed that the Raspberry Pi3 Video does not support 1920x1080 resolution. It's not caused by Ubuntu OS but it's the limitation of Raspberry Pi3 hardware. The Raspberry Pi3 is quite cheap and I will not set a high expectation. ;-)

Cheers,
Raymond

---

