---
title: "Wrong display resolution on wide screen"
date: 2017-04-02
forum: MINT
---

### Post by ekalips on 2017-04-02
Hi all. Recently I bought new monitor (16:9) and now I can't set it's resolution (1920x1080). I tried to update drivers, update system, and xrandr. Last one gave me this:

```
cvt -v 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync



xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA-0 1920x1080_60.00

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30

```


And this is result of ```
xrandr --currentScreen 
```
```
0: minimum 8 x 8, current 1024 x 768, maximum 16384 x 16384DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00*+
   1360x768      59.96    59.80  
   1152x864      60.00  
   800x600       72.19    60.32    56.25  
   680x384       59.96    59.80  
   640x480       59.94  
   512x384       60.00  
   400x300       72.19  
   320x240       60.05  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
  1920x1080_60.00 (0x2f4) 173.000MHz -HSync +VSync
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock  67.16KHz
        v: height 1080 start 1083 end 1088 total 1120           clock  59.96Hz



```

Can anybody help?

---

### Post by Autodave on 2017-04-03
We can try! :-)  First off, what video card are you using and where did you get the drivers for it from? Secondly, how is monitor connected to PC: what kind of cable: VGA, DVI, HDMI?

---

### Post by ekalips on 2017-04-03
I have Nvidia GTS 450 videoed. Monitor is connected via VGA. Drivers taken from official repositories.

---

### Post by Autodave on 2017-04-03
Can you connect the monitor via DVI cable or HDMI and try it?

---

### Post by ekalips on 2017-04-04
My videocard doesn't support HDMI, and monitor doesn't have DVI or HDMI neither. I can try with VGA-DVI adapter.

---

### Post by Autodave on 2017-04-04
Possibly try another VGA cable, too. Something tells me that a VGA cable will not go that high of resolution. I have also heard of weird problems with cheaper VGA cables.

---

### Post by gordintoronto on 2017-04-04
What is the brand and model of the monitor? Have you installed an Nvidia driver?

What version of Linux are you using? (Eg. 64-bit Ubuntu 16.04)

If you try a VGA-DVI adapter, things will only get worse.

---

### Post by ekalips on 2017-04-05
I'm using Linux Mint 18.1 (based on Ubuntu 16.04 LTS). Monitor is "LG Electronics W2243S-PF". And yes, I have latest Nvidia drivers, that provided by "Driver manager".

---

### Post by howefield on 2017-04-05
Thread moved to the "*MINT*" forum.

---

### Post by ekalips on 2017-05-11
Hi all. I found a solution!
You need to edit your xorg.conf (/etc/X11/xorg.conf). In "Monitor" part find HorizSync and VertRefresh and replace it with new values:
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
Now restart your PC (maybe you can restart only x server, but i don't know how to do it) and after it you'll find bunch of new resolutions in your display options. 
Hope this'll help someone!

---

### Post by mörgæs on 2017-05-11
Thanks for posting the solution.
If you mark the thread solved using Thread Tools there is a better chance that people will find it.

---

