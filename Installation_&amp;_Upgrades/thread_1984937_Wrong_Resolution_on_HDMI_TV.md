---
title: "Wrong Resolution on HDMI TV"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by Tiefschnee on 2012-05-22
Hey there,

I'm trying to connect my pc to a TV. The mainboard (Intel DH61DL) has an DVI-D exit, which I'm using with an HDMI adapter to connect to a Sharp TV.

When I turn on the computer the picture is fine, I can enter the bios and so on. But when it starts booting the OS the screen turns dark.

If I connect an additional screen to the computer, I see that the TV has the wrong resolution, 720x570. Insead of 1920x1080. In the drop down menu is nothing else to select.

The screen is identified as an Sharp Corporation 37", which is basically correct.

I have no idea what I can do about that. I'm very grateful for any hint and tip!

-peter

---

### Post by papibe on 2012-05-22
Hi Tiefschnee.

Could you post the content of these files right after a boot with the TV connected?
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Please paste separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the links here.

Regards.

---

### Post by Tiefschnee on 2012-05-22
Thank you very much for the quick reply.

The first file isn't there, I also couldn't find it in a different direction. But the second is here:
[FONT=monospace]
[/FONT]Xorg.0.log:
[http://paste.ubuntu.com/1001490/](http://paste.ubuntu.com/1001490/)

-peter

---

### Post by papibe on 2012-05-22
I took the TV's edid:
```
[     3.963] (II) intel(0): EDID (in hex):
[     3.963] (II) intel(0): 	00ffffffffffff004d10c70f01010101
[     3.963] (II) intel(0): 	0010010380522e782a1bbea25534b326
[     3.963] (II) intel(0): 	144a5200000001010101010101010101
[     3.963] (II) intel(0): 	010101010101011d80d0721c1620102c
[     3.963] (II) intel(0): 	258034cd3100009e8c0ad08a20e02d10
[     3.963] (II) intel(0): 	103e960034cd31000018000000fc0053
[     3.963] (II) intel(0): 	484152502048444d490a2020000000fd
[     3.963] (II) intel(0): 	00313d0f2e08000a20202020202001bd
[     3.963] (II) intel(0): 	020321714d9405130411120203151606
[     3.963] (II) intel(0): 	0701230907078301000066030c001000
[     3.963] (II) intel(0): 	808c0ad090204031200c40550034cd31
[     3.963] (II) intel(0): 	000018011d8018711c1620582c250034
[     3.963] (II) intel(0): 	cd3100009e011d00bc52d01e20b82855
[     3.963] (II) intel(0): 	4034cd3100001e011d007251d01e206e
[     3.963] (II) intel(0): 	28550034cd3100001e00000000000000
[     3.963] (II) intel(0): 	0000000000000000000000000000009b
```

and got this information:
```
	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fc
	Identifier "SHARP HDMI"
	VendorName "SHP"
	ModelName "SHARP HDMI"
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
	HorizSync 15-46
	VertRefresh 49-61
	# Max dot clock (video bandwidth) 80 MHz
	# DPMS capabilities: Active off:yes  Suspend:no  Standby:no

	Mode 	[COLOR="Red"]**"1920x540"**[/COLOR]	# vfreq 50.044Hz, hfreq 28.125kHz
		DotClock	74.250000
		HTimings	1920 1968 2012 2640
		VTimings	540 542 547 562
		Flags	"Interlace" "+HSync" "+VSync"
	EndMode
	Mode 	"720x480"	# vfreq 59.940Hz, hfreq 31.469kHz
		DotClock	27.000000
		HTimings	720 736 798 858
		VTimings	480 489 495 525
		Flags	"-HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
EndSection

```
That's a very odd resolution (check marked red text).

Do you have a way to verify your TV's resolution? Like a manual or in the TV manufacture site (I mean the actual display size)?

Another options would be that the info is corrupted. Have you tried another input?

Regards.

---

### Post by Tiefschnee on 2012-05-22
thank you very much for your efforts!

The manual acutally doesn't say anything [http://www.tradenet.sharp.co.uk/tech/fromcorp.asp?ID=95924](http://www.tradenet.sharp.co.uk/tech/fromcorp.asp?ID=95924)

but a store that sells it says it can 1080i and 720p.

---

### Post by Tiefschnee on 2012-05-22
Actually I did find something saying:

Number of dots 1,555,200 dots (960 x 540 x 3 dots)

---

### Post by papibe on 2012-05-22
Could you open a terminal on the TV and post the results of this command?
```
xrandr
```
Regards.

---

### Post by Tiefschnee on 2012-05-22
sure:

```
Screen 0: minimum 320 x 200, current 2320 x 1200, maximum 8192 x 8192
VGA1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 432mm x 324mm
   1600x1200      60.0*+
   1280x1024      75.0     60.0  
   1280x960       75.0     60.0  
   1152x864       75.0  
   1024x768       85.0     75.1     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI1 connected 720x576+1600+0 (normal left inverted right x axis y axis) 820mm x 461mm
   720x576        50.0* 
   720x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by papibe on 2012-05-22
Try this:
```
xrandr --newmode "1920x540_50"  **[COLOR="Red"]74.25[/COLOR]**  1920 1968 2012 2640  540 542 547 562  +HSync +VSync
```

And then:
```
xrandr --addmode HDMI1 "1920x540_50"
```
Tell us how it goes.
Regards.

---

### Post by Tiefschnee on 2012-05-22
wow. thank you so much. But is it possible that there is a typo hidden in the first line?

I only get:

usage: xrandr [options]
  where options are:
  -display <display> or...

---

### Post by papibe on 2012-05-22
Oops, I missed one parameter, I edited my post above.

Regards.

---

### Post by Tiefschnee on 2012-05-22
After the modes name was the frequency missing. I put 50 there, but that doesn't work. As I'm in Europe, shouldn't that be 60 anyway?

---

### Post by Tiefschnee on 2012-05-22
unfortunately it didn't work. But shouldn't it be something with the resolution of 960x540?

---

### Post by papibe on 2012-05-22
> **Tiefschnee said:**
> unfortunately it didn't work. But shouldn't it be something with the resolution of 960x540?

That modeline doesn't seem to be available. Here are more from your own log:
```
Modeline "1920x1080i"   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync

Modeline "720x480"   27.00  720 736 798 858  480 489 495 525 -hsync -vsync

Modeline "1280x720"   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync
```
Try them, and see how it goes.
Regards.

---

### Post by Tiefschnee on 2012-05-23
Thank you very much for your help and patience.

Unfortunately nothing worked - I tried all the configs from the log file.

I even tried windows from another disc, which worked also in a strange way. The picture was shown properly, the TV claimed to see 1080i 50 Hz but the actual Windows resolution was 640x480. Then I installed the proper graphics driver and after a reboot the screen stayed dark - which was the end of the windows tryout...

Here I read that interlaced video output is not supported: [http://lists.freedesktop.org/archives/intel-gfx/2012-January/014490.html](http://lists.freedesktop.org/archives/intel-gfx/2012-January/014490.html)

I also connected the PC to the TV without any other screen attached and tried to change resolutions remoltly - focusing on the 720p ones from the log file. But also here nothing worked out.

As it's not my TV, and I only use it for another 4 months, I decided to use VGA port of the TV and stretch the image to full screen and adjust the pixel ratio on the computer to 0.75.
It's not ideal, but well, it works for now...

Anyway, again thank you very much! I learned quite a bit during the process. I really appreciate it!

-peter

---

