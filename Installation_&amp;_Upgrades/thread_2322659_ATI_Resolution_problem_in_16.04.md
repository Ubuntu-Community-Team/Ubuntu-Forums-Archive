---
title: "ATI Resolution problem in 16.04"
date: 2016-04-29
forum: Installation &amp; Upgrades
---

### Post by jellybaby on 2016-04-29
Hi,

I've just upgraded to 16.04 LTS from 14.04 LTS. 

[SIZE=4]_Problem:_[/SIZE]

I can't change the resolution to 1280x1024 which is the native res. for my monitor; the highest available res. is 1024x768.

[SIZE=4]_Attempted fixes:_[/SIZE]

I put the xorg.conf file from my 14.04 installation in the /etc/X11 folder, but no joy;

I tried installing the AMD driver (amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run); it installed fine, but after restarting the PC crashed. I reinstalled 16.04 LTS.

[SIZE=4]_Here my info:_[/SIZE]

2x AMD Athlon II X2 245 Processor;
Gallium 0.4 on AMD RS880 (DRM 2.43.0, LLVM 3.8.0) (ATI Radeon HD4200 integrated on an ASUS M4A785-M motherboard);
2 GB RAM (the video chip uses 256 MB of that, so usable RAM is 1792 MB).

[SIZE=4]_Output of xrandr:_[/SIZE]

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
DVI-0 disconnected (normal left inverted right x axis y axis)

I read [here]("https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/") that AMD will be bringing out new drivers later this year, but surely the driver that Xenial uses should be capable of changing resolution?

I hope someone has a bright idea!

Regards

---

### Post by mörgæs on 2016-04-30
There might be a solution for 16.04 but in this case it seems like the easiest approach is to carry on with 14.04. I understand the desire to use the latest software available but it might take some time before the open source ATI drivers have caught up with the closed source ones.

---

### Post by jellybaby on 2016-04-30
Thanks for the answer, mörgæs.

Yes, I think you're probably right. I will reinstall 14.04 alongside 16.04, I guess. That way, I can try out things without endangering my work.

---

### Post by jellybaby on 2016-07-28
Hi,

I just thought I'd share the fix I use on 16.04 using the "cvt" tool and "xrandr":

in a terminal, I type

```
**cvt 1280 1024**
```

That gives me the following:

```
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

I then type 

```
**xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync**
``` (this is everything that comes after "Modeline")

then

```
**xrandr --addmode VGA-0 1280x1024_60.00**
``` (VGA-0 is my video device)

and it works instantly.

Of course, I have to run it every time I log in, but I wrote an executable script that I can just double-click.

Cheers!

---

### Post by jellybaby on 2016-08-07
Hi,

mörgæs suggested I mark this thread as solved. It's a good idea, so I will.

Just for interest's sake by the way, now that this resolution problem is solved, I have completely switched over to Ubuntu xenial; after putting in 4 more gigs of ram, Unity runs much more quickly and smoothly. I'll be able to work on this old PC for years!

Regards

---

