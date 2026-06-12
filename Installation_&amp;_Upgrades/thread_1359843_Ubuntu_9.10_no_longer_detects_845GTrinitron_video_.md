---
title: "Ubuntu 9.10 no longer detects 845G/Trinitron video settings"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by Silvestro Fantacci on 2009-12-20
I am trying to move from Ubuntu 9.04 (Jaunty Jackalope) to 9.10 (Karmic Koala).

I have the following hardware:

- PC: IBM NetVista PC 8318-31G
- Video Card: Intel(R) 845G/845GL/845GE
- Monitor: Dell Trinitron

In Ubuntu 9.04 the proper video settings were displayed and could be selected.

However after intalling Ubuntu 9.10 (from scratch), only the 800x600 and 640x480 video settings are shown (ref. System --> Preferences --> Display).

The monitor is shown as Unknown.

Then if I unplug the Trinitron monitor and plug in another monitor (while Ubuntu is running), the new monitor is recognised and the additional video settings, such as 1024x768 and 1280x1024 can be selected.

On selecting e.g. 1280x1024 and then plugging in the Trinitron monitor again, Ubuntu maintains that setting, which works OK.

However on rebooting to PC I am back to the 800x600 and 640x480 video settings.

Is there a way to fix this problem?

---

### Post by Silvestro Fantacci on 2009-12-27
Problem solved :)

I found this post by Giblet5 which helped me fix the problem:
[http://ubuntuforums.org/showthread.php?t=1324239](http://ubuntuforums.org/showthread.php?t=1324239)

Some details on what I did:

Graphics card: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
Monitor: Dell - Trinitron CRT - Model D1626HT (UltraScan 1600HS Series)

From the monitor's specifications:
[http://support.ap.dell.com/support/edocs/monitors/55347/specs.htm](http://support.ap.dell.com/support/edocs/monitors/55347/specs.htm)

HorizSync    31 - 107
VertRefresh  48 - 160

I added those two lines to the xorg.conf file, which I placed in the File System /etc/X11 folder.

On reboot the following screen resolutions became available:

640 x 350 (9:5) @ 84 85 ==> Loses Sync
640 x 400 (16:10) @ 85 ==> Loses Sync
720 x 400 (9:5) @ 85 ==> Loses Sync
640 x 480 (4:3) @ 60 73 75 85 ==> Loses Sync
800 x 600 (4:3) @ 56 60 72 75 85 ==> OK
832 x 624 (4:3) @ 75 ==> Loses Sync
1024 x 768 (4:3) @ 60 70 75 85 ==> OK
1152 x 864 (4:3) @ 60 70 75 85 100 ==> OK
1360 x 768 (16:9) @ 60 ==> Bad Aspect Ratio
1280 x 960 (4:3) @ 60 85 ==> OK
1440 x 900 (16:10) @ 60 ==> Bad Aspect Ratio
1280 x 1024 (5:4) @ 60 75 85 ==> OK
1400 x 1050 (4:3) @ 60 70 75 85 ==> OK
1600 x 1024 (3:2) @ 60 ==> Bad Colours
1680 x 1050 (16:10) @ 60 70 75 85 ==> Bad Aspect Ratio
1600 x 1200 (4:3) @ 60 65 70 75 85 ==> OK
1792 x 1344 (4:3) @ 60 75 ==> OK
1856 x 1392 (4:3) @ 60 ==> OK
1920 x 1440 (4:3) @ 60 ==> OK
2048 x 1536 (4:3) @ 60 ==> OK

I tested them and noted that only a subset worked OK.

For the resolutions that worked, I used cvt to get the relative modelines. I just used the 60 Hz frequency for all of them (no flickering noted). Here's what I got:

# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
# 1152x864 59.96 Hz (CVT 1.00M3) hsync: 53.78 kHz; pclk: 81.75 MHz
Modeline "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync
# 1280x960 59.94 Hz (CVT 1.23M3) hsync: 59.70 kHz; pclk: 101.25 MHz
Modeline "1280x960_60.00"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
# 1400x1050 59.98 Hz (CVT 1.47M3) hsync: 65.32 kHz; pclk: 121.75 MHz
Modeline "1400x1050_60.00"  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync
# 1600x1200 59.87 Hz (CVT 1.92M3) hsync: 74.54 kHz; pclk: 161.00 MHz
Modeline "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
# 1792x1344 60.00 Hz (CVT 2.41M3) hsync: 83.57 kHz; pclk: 203.25 MHz
Modeline "1792x1344_60.00"  203.25  1792 1920 2112 2432  1344 1347 1351 1393 -hsync +vsync
# 1856x1392 59.93 Hz (CVT 2.58M3) hsync: 86.48 kHz; pclk: 217.25 MHz
Modeline "1856x1392_60.00"  217.25  1856 1992 2184 2512  1392 1395 1399 1443 -hsync +vsync
# 1920x1440 59.97 Hz (CVT 2.76M3) hsync: 89.53 kHz; pclk: 233.50 MHz
Modeline "1920x1440_60.00"  233.50  1920 2064 2264 2608  1440 1443 1447 1493 -hsync +vsync
# 2048x1536 59.95 Hz (CVT 3.15M3) hsync: 95.45 kHz; pclk: 267.25 MHz
Modeline "2048x1536_60.00"  267.25  2048 2208 2424 2800  1536 1539 1543 1592 -hsync +vsync

I then edited xorg.conf, commented out HorizSync and VertRefresh, added the above Modeline commands and rebooted - so that the resolutions that do not work are no longer selectable (I couldn't figure out how to remove the 640x480 resolution nor how to make it work, so I just gave up and devoted a Modeline to it).

---

