---
title: "Unable to set resolution to 1440x900"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by citronax on 2011-07-16
Morning,

I have installed Ubuntu 11.04 on my Dell Latitude D610 (with ATI X300 graphics card) and am trying to set the default resolution to 1440x900 for my Samsung Syncmaster 931 monitor.  I have installed "fglrx" and when I run "xrandr -q" I get the following information.

```

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1440 x 1440
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 410mm x 257mm
   1440x900       59.9 +   75.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   800x600        59.9  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

```When I then run "xrandr - s 1440x900" I get the following message:
```

Size 1440x900 not found in available modes

```What am I doing wrong here.  Other posts say I need to edit "etc/x11/xorg.conf" but this file does not appear to exist.

Any help is greatly appreciated with this.

Regards,

Citronax

---

### Post by realzippy on 2011-07-16
1. fglrx does not work for your card anymore.
See red box on:
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)
   You should uninstall it,following instructions on that page.
2. when you have done this,try:

```
xrandr --output VGA-0 --mode 1440x900
```

3.Welcome to UF!

---

### Post by steve11911 on 2011-07-16
First, I would check the EXACT model number of your monitor...There are several.Some support this resolution and some don't.
The 'not found in available modes' may mean you;ll have to add the mode.
This page,
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
near the bottom under "Adding undetected resolutions" will explain this better than I can.

---

### Post by realzippy on 2011-07-16
> **steve11911 said:**
> First, I would check the EXACT model number of your monitor...There are several.Some support this resolution and some don't.
The 'not found in available modes' may mean you;ll have to add the mode.
This page,
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
near the bottom under "Adding undetected resolutions" will explain this better than I can.

??
Which samsung 931 does not support this resolution?
It is the native resolution of this panel.
And the very **first** thing to do is to clean up the fglrx mess because it might also affect the free ati driver.
Also OP tried xrandr;note that he seems to have 2 monitors connected (VGA-0 and LVDS),so he had to specify  panel in his
xrandr -s attempt,as I have suggested.



@ OP
Worth testing might also be disconnecting the second monitor;maybe the virtual screen size is not enough for both.

---

### Post by citronax on 2011-07-16
Thanks for the info realzippy.  After a bit of a struggle I managed to get this sorted.  The only other thing I had to do was to add the last line of your answer to "/etc/GDM/Init/Default" to get the required resolution to persist.

I now need to look at why the display seems to have a 10214x768 window in it and is not initially making full use of the set resolution.

Once again thanks for your help.

---

### Post by realzippy on 2011-07-16
*now need to look at why the display seems to have a 1024x768 window in it and is not initially making full use of the set resolution.*

..can you explain more,I don' t understand exactly...?

---

### Post by steve11911 on 2011-07-16
Before I posted earlier some homework had revealed that:

the 931c has a max resolution of 1280x1024

[http://www.superwarehouse.com/Samsung_SyncMaster_931C_19_Black_LCD_Monitor/SYNCMASTER_931C/p/1488891](http://www.superwarehouse.com/Samsung_SyncMaster_931C_19_Black_LCD_Monitor/SYNCMASTER_931C/p/1488891)

931B is the same:

[http://reviews.cnet.com/lcd-monitors/samsung-syncmaster-931b-black/4507-3174_7-32064847.html](http://reviews.cnet.com/lcd-monitors/samsung-syncmaster-931b-black/4507-3174_7-32064847.html)

931BF the same:

[http://www.samsung.com/sg/consumer/pc-peripherals-printer/monitor/lcd-monitor/LS19MEDSSQ/XSS/index.idx?pagetype=prd_detail&tab=specification](http://www.samsung.com/sg/consumer/pc-peripherals-printer/monitor/lcd-monitor/LS19MEDSSQ/XSS/index.idx?pagetype=prd_detail&tab=specification)

The 931BW DOES support 1440x900:

[http://www.afterdawn.com/products/product_details.cfm/1777/samsung_syncmaster_931bw](http://www.afterdawn.com/products/product_details.cfm/1777/samsung_syncmaster_931bw)

====
I futzled with this problem myself and over about 4 days became a near expert on what DOESN'T work.My LVDS [Laptop] supports 1280x1024 and my external monitor which interestingly is designated VGA1 will go higher.After following the advice on the page I previously linked and a few reboots-Success!Now my external is stable at the highest resolution.

Thanks for the Easystroke link-Very Nice! Is that easy to master?

---

### Post by citronax on 2011-07-17
Morning All,

To clarify my last post I have attached to screen shots, one with nothing open where you can see the original 1024x768 frame and one with Firefox maximized (To fully maximize Firefox I have to move it to the right, outside of the original 1024x768 frame).

Any help is greatly appreciated.

Regards,

Citronax

---

### Post by realzippy on 2011-07-17
@ citronax

Do I get you right,the laptop's monitor still runs at
1024x768
although it's native resolution is 1440x900 ?
The pics you posted are from the 2nd monitor(syncmaster),placed
right-off your laptop panel?

If this is correct,I suggest to "addmode" 1440x900 to LVDS by a
modeline created with *cvt* running *xrandr*.
Feel free to ask although it is described in steve's [link]("https://wiki.ubuntu.com/X/Config/Resolution").


@ steve

Have to apologize,was sure all ss931 where 19" widescreens with
1440x900.Sorry,was wrong indeed.
Yep,easystroke is fun to set up.It takes some time to get
used to the gestures,but,after a few days you miss it horribly when
working on a machine without mouse-gestures.It speeds up your
work-flow drastically....

---

