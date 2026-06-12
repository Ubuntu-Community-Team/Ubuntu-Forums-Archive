---
title: "Please Help: Screen Resolution 9.10 S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by jdier on 2009-11-25
I have an older machine that I am having difficulties getting screen resolution correct on.  I have a monitor that wants 1280x1024 and an onboard graphics card that supports it, however when I install and boot xubuntu only shows me 800x600 and lower.

I originally did an upgrade from 8.04 and saw these problems, but the info below is all from a fresh install of 9.04 which has been upgraded (via update manager) to 9.10.  (just as a note I did live CD of standard ubuntu 9.10 and still had low res graphics)

I have successfully worked through a similar problem on an integrated intel graphics machine, but when I followed similar steps here I failed.

Everything appears to work perfectly right up until the last command.

```
jdier@Ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

```



```

jdier@Ubuntu:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  

jdier@Ubuntu:~$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

jdier@Ubuntu:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

jdier@Ubuntu:~$ xrandr --addmode default 1280x1024_60.00

jdier@Ubuntu:~$ xrandr --output default --mode 1280x1024_60.00 --verbose
xrandr: screen cannot be larger than 800x600 (desired size 1280x1024)

jdier@Ubuntu:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 1280 x 1024
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
   1280x1024_60.00   59.9  

jdier@Ubuntu:~$ xrandr --output default --mode 1280x1024_60.00 --verbose
screen 0: 1280x1024 339x271 mm  95.85dpi
crtc 0: 1280x1024_60.00   59.9 +0+0 "default"
xrandr: Configure crtc 0 failed
crtc 0: disable
screen 0: revert
crtc 0: revert
jdier@Ubuntu:~$ 
```

---

### Post by jdier on 2009-12-03
Anyone out there willing/able to help?

---

### Post by pentagon on 2009-12-23
Unfortunately, I stuck with the same problem. After upgrade from SuSe 10.1 to Karmic I can't get my computer display to work with a proper resolution.

---

### Post by Silvestro Fantacci on 2009-12-27
I also had the problem and this worked for me:
[http://ubuntuforums.org/showthread.php?t=1324239](http://ubuntuforums.org/showthread.php?t=1324239)

---

