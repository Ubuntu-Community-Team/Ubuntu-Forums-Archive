---
title: "after 11.04 upgrade second monitor not working"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by neiljansons on 2011-04-30
I have a Dell Inspiron 6400 laptop that has been through many upgrades of Ubuntu but was working well under 10.10
In my office I have a second monitor attached and I also sometimes use a data projector as a second monitor. Even though I had problems in previous versions in 10.10 it worked very well.
After the upgrade to 11.04 both screens have a distorted image a bit like an old television when the horizontal hold is out. However some dialogue boxes would appear through the haze often just with the buttons or boxes appearing.
As soon as I unplug the second monitor the laptop screen is perfect. I need to get the second monitor working though.
Any ideas?

---

### Post by neiljansons on 2011-04-30
I tried a different external monitor with different results.
This time the background image on the main screen disappears and while images and programmes will load on both monitors the screen will not refresh properly - if you close something it still appears there.

Would it be possible to restore the video configuration from before the upgrade? I have backups that hopefully would include it.

---

### Post by neiljansons on 2011-05-02
Next I tried booting up on an image cd of 11.04
Subtly different results but clearly there is a problem with 11.04 and my hardware with a second monitor that there wasn't with 10.10

Apart from reinstalling with 10.10 is there anything else I can do?

---

### Post by blu3cheez on 2011-05-02
This solution could work for you:

[http://ubuntuforums.org/showthread.php?t=1742284](http://ubuntuforums.org/showthread.php?t=1742284)

---

### Post by neiljansons on 2011-05-03
thanks for your help

I tried restoring ~/.config/monitors.xml from a backup before the upgrade from 10.10 to 11.04 but there is no difference that I can see.

With one of the monitors it sort of works. That is things appear on both screens ok but something to do with the refresh is wrong. The desktop is black with no background picture or icons showing. If you minimise a window (on either screen) the window stays painted on the screen and general screen reaction is slow.

Here is the xrandr
```
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 4096 x 4096
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0 +   75.0* 
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
TV1 unknown connection (normal left inverted right x axis y axis)
   848x480        30.0 +
   640x480        30.0 +
   1024x768       30.0  
   800x600        30.0  

```

What is TV1? I don't recall noticing that before? Can I get rid of it? How?

---

### Post by srigelsford on 2011-05-18
I have the same issue after an upgrade from 10.10.
Interestingly when I disable my second monitor it is detected fine. As soon as I try to use it, it changes it's mind:

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 connected (normal left inverted right x axis y axis)
   2048x1152      59.9 +
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0  
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)


Screen 0: minimum 320 x 200, current 2048 x 1952, maximum 8192 x 8192
VGA1 connected 2048x1152+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
LVDS1 connected 1280x800+322+1152 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)
  2048x1152 (0xb5)  156.8MHz
        h: width  2048 start 2096 end 2128 total 2208 skew    0 clock   71.0KHz
        v: height 1152 start 1155 end 1160 total 1185           clock   59.9Hz

---

### Post by neiljansons on 2011-09-21
I gather this this second monitor not working is as a result of unity.
The only answers that seem to be around are to remove unity in order to get the second monitor working.
If unity is going to be the new environment this doesn't seem to be much of an answer.
Will this problem be fixed in 11.10?

---

