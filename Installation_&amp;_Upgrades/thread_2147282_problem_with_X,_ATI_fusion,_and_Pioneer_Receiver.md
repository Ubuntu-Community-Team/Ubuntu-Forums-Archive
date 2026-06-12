---
title: "problem with X, ATI fusion, and Pioneer Receiver"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by chene on 2013-05-21
hi all,

I've recently upgraded from 12.04 to 12.10 for the purpose of the integrated ATI driver with the intention to set up a fully functional XBMC media center.  According to [http://youresuchageek.blogspot.fr/2012/06/xbmc-install-and-config-howto-for-linux.html](http://youresuchageek.blogspot.fr/2012/06/xbmc-install-and-config-howto-for-linux.html), ubuntu 12.10 is preferred over other version (either 12.04 0r 13.04) due to the integrated driver.  However, I am having a hard time setting up the proper Xorg file for it to detect my projector/receiver properly.  I seek your help.

(NOTE:  Previously I followed the guide at [http://youresuchageek.blogspot.fr/2012/06/xbmc-install-and-config-howto-for-linux.html](http://youresuchageek.blogspot.fr/2012/06/xbmc-install-and-config-howto-for-linux.html) and had ubuntu 12.04 working with manually installed ATI catalyst 12.9 working **WITHOUT** manually adjusting X)

First off, my hardware:

AMD fusion E350, connected to
Pioneer VSX-1022 receiver via HDMI
Benq 1080p projector at 1920x1080@60Hz

hardware info:

```
:~$ lspci|grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]

```
```
:~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: AMD ATOMBIOS
vendor: (C) 1988-2010, AMD Technologies Inc.
product: WRESTLER 01.00
memory: 16384kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x256
mode: 1024x768x256
mode: 1280x1024x256
mode: 640x480x32k
mode: 640x480x64k
mode: 800x600x32k
mode: 800x600x64k
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 320x200x32k
mode: 320x200x64k
mode: 1600x1200x256
mode: 1600x1200x32k
mode: 1600x1200x64k
edid:
edid: 1 3
id: 0000
eisa: PIO0000
serial: 01010101
manufacture: 0 2012
input: analog signal.
screensize: 0 0
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 800x600@85
ctiming: 1024x768@85
ctiming: 1280x1280@85
ctiming: 1280x1024@85
ctiming: 1400x1050@60
ctiming: 1440x1440@60
ctiming: 1600x1200@60
ctiming: 1920x1200@60
dtiming: 1920x1080@67
dtiming: 720x480@59
monitorrange: 31-91, 48-86
monitorname: VSX-1022

```

What puzzled me is the fact that it detected my reciver at 1920x1080@**67Hz**, instead of 60Hz.  When I starts X, it kept on flicking the display, switching between commandline mode and graphics mode.

X logs shows:

```

[   843.838] (II) fglrx(0): EDID vendor "SAM", prod id 27
[   843.838] (II) fglrx(0): Using hsync ranges from config file
[   843.838] (II) fglrx(0): Using vrefresh ranges from config file
[   843.838] (II) fglrx(0): Printing DDC gathered Modelines:
[   843.838] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[   843.838] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   843.838] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   843.838] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   843.838] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   843.838] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   843.838] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   843.838] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   843.838] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   843.838] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   843.838] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   843.838] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   843.838] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   843.838] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   843.838] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   843.838] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)

```

And the best I can do is to get X to display at 1280x1024@60Hz.

Can anyone gives an insight as how to set it up to display at a proper 1080p@60Hz?

thanks in advance,

---

### Post by dino99 on 2013-05-21
HorizSync & VertRefresh might help to force using 60 hz

[http://www.x.org/wiki/FAQVideoModes](http://www.x.org/wiki/FAQVideoModes)

---

