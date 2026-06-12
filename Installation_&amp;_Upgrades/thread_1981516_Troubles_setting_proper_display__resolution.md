---
title: "Troubles setting proper display  resolution"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by SeregaI on 2012-05-16
Hello community,

I am fresh for Ubuntu and Linux in general. I have installed Ubuntu 12.04 and stuck trying to setup correct resolution for my LCD display.
The native resolution for the LCD is 1920x1080

here is the output from xrandr:
> 
$xrandr
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 4096 x 4096
LVDS1 connected 1280x720+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x720       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)Then I create new modeline:
> 
$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsyncSo far so good.

then I create new mode using xrandr:

> $ xrandr --newmode "1920x1080_60.00" 173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsyncBut for some reason that new  mode  was created for VGA (VGA1) output instead of LCD output (LVDS1):
> $ xrandr
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 4096 x 4096
LVDS1 connected 1280x720+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x720       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
  1920x1080_60.00 (0xbc)  173.0MHz   <---------- ????!!!!!!
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0HzSo, if I try to add mode to LVDS1, I get an error:

> $ xrandr --addmode LVDS1 "1920x1080_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26Adding that new  mode to VGA1 works fine, but I don't use that VGA1  output.

---

