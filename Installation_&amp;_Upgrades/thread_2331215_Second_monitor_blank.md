---
title: "Second monitor blank"
date: 2016-07-19
forum: Installation &amp; Upgrades
---

### Post by mps69 on 2016-07-19
Setup
Ubuntu 16.04 - 64bit
Memory 7GB
Processor AMD A6-6400K APU Radeon
Graphic Gallium 0.4 on AMD ARUBA
Two monitors

I think I've previously posted this in the wrong section, so I'll see if I can get a response here.

So i've got a new PC, details above, I tested the build with a live USB, and all was fine. Install went well and smoothly.
The only problem I've got is with my second monitor. Both are using VGA, but the main monitor is going via a HDMI convertor.
The second monitor is just stright VGA connection.
When I boot, both monitors power up. However after a few seconds the second one drops the signal and seems to go to sleep.
When I go into setting, both are recognised, and I can move the mouse to the second one. I've even had the case of an application opening on this one.
The only thing that seems to make it switch on is to suspend the session, then bring it out of hibernation. At this point the second monitor starts working.....weird I know.
Now I've searched around, and couldn't find a definitive answer to what the issue is, so i'm hoping someone with a little more knowledge will be able explain how I can fix it.
Thanks

Output from xrandr --verbose
```
Screen 0: minimum 320 x 200, current 2880 x 1024, maximum 16384 x 16384
HDMI-0 connected primary 1600x900+1280+0 (0x57) normal (normal left inverted right x axis y axis) 443mm x 249mm
	Identifier: 0x53
	Timestamp:  48949
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0 1 2 3
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID: 
		00ffffffffffff0005e3362064740100
		29140103802c19782ab815a6554b9b25
		135054bfee0081c0a9c0010101010101
		010101010101302a40c8608464301850
		1300bbf91000001e000000fd00374b1e
		530e000a202020202020000000fc0032
		3033360a2020202020202020000000ff
		0051383141414841323935333332018d
		02031b61230907078301000067030c00
		2000802d43908402e2000f8c0ad08a20
		e02d10103e9600a05a00000000000000
		00000000000000000000000000000000
		00000000000000000000000000000000
		00000000000000000000000000000000
		00000000000000000000000000000000
		00000000000000000000000000000029
	output_csc: bypass 
		supported: bypass, tvrgb, ycbcr601, ycbcr709
	audio: auto 
		supported: off, on, auto
	scaling mode: None 
		supported: None, Full, Center, Full aspect
	dither: off 
		supported: off, on
	underscan vborder: 0 
		range: (0, 128)
	underscan hborder: 0 
		range: (0, 128)
	underscan: off 
		supported: off, on, auto
	coherent: 1 
		range: (0, 1)
  1600x900 (0x57) 108.000MHz +HSync +VSync *current +preferred
        h: width  1600 start 1624 end 1704 total 1800 skew    0 clock  60.00KHz
        v: height  900 start  901 end  904 total 1000           clock  60.00Hz
  1920x1080 (0x58) 148.500MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1920x1080 (0x59) 148.352MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.43KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  59.94Hz
  1280x720 (0x5a) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1280x720 (0x5b) 74.176MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  44.96KHz
        v: height  720 start  725 end  730 total  750           clock  59.94Hz
  1024x768 (0x5c) 78.800MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock  60.06KHz
        v: height  768 start  769 end  772 total  800           clock  75.08Hz
  1024x768 (0x5d) 75.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock  56.48KHz
        v: height  768 start  771 end  777 total  806           clock  70.07Hz
  1024x768 (0x5e) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  832x624 (0x5f) 57.284MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock  49.73KHz
        v: height  624 start  625 end  628 total  667           clock  74.55Hz
  800x600 (0x60) 50.000MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock  48.08KHz
        v: height  600 start  637 end  643 total  666           clock  72.19Hz
  800x600 (0x61) 49.500MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock  46.88KHz
        v: height  600 start  601 end  604 total  625           clock  75.00Hz
  800x600 (0x62) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x63) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  720x480 (0x64) 27.027MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.50KHz
        v: height  480 start  489 end  495 total  525           clock  60.00Hz
  720x480 (0x65) 27.000MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.47KHz
        v: height  480 start  489 end  495 total  525           clock  59.94Hz
  640x480 (0x66) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock  37.50KHz
        v: height  480 start  481 end  484 total  500           clock  75.00Hz
  640x480 (0x67) 31.500MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock  37.86KHz
        v: height  480 start  489 end  491 total  520           clock  72.81Hz
  640x480 (0x68) 30.240MHz -HSync -VSync
        h: width   640 start  704 end  768 total  864 skew    0 clock  35.00KHz
        v: height  480 start  483 end  486 total  525           clock  66.67Hz
  640x480 (0x69) 25.200MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
        v: height  480 start  490 end  492 total  525           clock  60.00Hz
  640x480 (0x6a) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
  720x400 (0x6b) 28.320MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock  31.47KHz
        v: height  400 start  412 end  414 total  449           clock  70.08Hz
VGA-0 connected 1280x1024+0+0 (0x6c) normal (normal left inverted right x axis y axis) 337mm x 270mm
	Identifier: 0x54
	Timestamp:  48949
	Subpixel:   no subpixels
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       1
	CRTCs:      0 1 2 3
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID: 
		00ffffffffffff004293a5069f130400
		090f010368221b962a6e06a1544c9926
		194f54bfef0001010101010101018180
		000000000000302a009851002a403070
		1300510e1100001ec31e002041002030
		10601300510e11000000000000fd003c
		4b1e500e000a202020202020000000ff
		00463557513532303236373136370035
	output_csc: bypass 
		supported: bypass, tvrgb, ycbcr601, ycbcr709
	scaling mode: None 
		supported: None, Full, Center, Full aspect
	load detection: 1 
		range: (0, 1)
  1280x1024 (0x6c) 108.000MHz +HSync +VSync *current +preferred
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x1024 (0x6d) 135.000MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock  79.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  75.02Hz
  1024x768 (0x5c) 78.800MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock  60.06KHz
        v: height  768 start  769 end  772 total  800           clock  75.08Hz
  1024x768 (0x6e) 78.750MHz -HSync -VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock  60.02KHz
        v: height  768 start  769 end  772 total  800           clock  75.03Hz
  1024x768 (0x5d) 75.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock  56.48KHz
        v: height  768 start  771 end  777 total  806           clock  70.07Hz
  1024x768 (0x5e) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  832x624 (0x5f) 57.284MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock  49.73KHz
        v: height  624 start  625 end  628 total  667           clock  74.55Hz
  800x600 (0x60) 50.000MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock  48.08KHz
        v: height  600 start  637 end  643 total  666           clock  72.19Hz
  800x600 (0x61) 49.500MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock  46.88KHz
        v: height  600 start  601 end  604 total  625           clock  75.00Hz
  800x600 (0x62) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x63) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x66) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock  37.50KHz
        v: height  480 start  481 end  484 total  500           clock  75.00Hz
  640x480 (0x67) 31.500MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock  37.86KHz
        v: height  480 start  489 end  491 total  520           clock  72.81Hz
  640x480 (0x68) 30.240MHz -HSync -VSync
        h: width   640 start  704 end  768 total  864 skew    0 clock  35.00KHz
        v: height  480 start  483 end  486 total  525           clock  66.67Hz
  640x480 (0x69) 25.200MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
        v: height  480 start  490 end  492 total  525           clock  60.00Hz
  720x400 (0x6b) 28.320MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock  31.47KHz
        v: height  400 start  412 end  414 total  449           clock  70.08Hz
DVI-0 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x55
	Timestamp:  48949
	Subpixel:   horizontal rgb
	Clones:    
	CRTCs:      0 1 2 3
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	output_csc: bypass 
		supported: bypass, tvrgb, ycbcr601, ycbcr709
	audio: auto 
		supported: off, on, auto
	scaling mode: None 
		supported: None, Full, Center, Full aspect
	dither: off 
		supported: off, on
	underscan vborder: 0 
		range: (0, 128)
	underscan hborder: 0 
		range: (0, 128)
	underscan: off 
		supported: off, on, auto
	coherent: 1 
		range: (0, 1)
```

---

