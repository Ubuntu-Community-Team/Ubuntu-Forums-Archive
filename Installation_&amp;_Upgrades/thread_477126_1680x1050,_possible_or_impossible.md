---
title: "1680x1050, possible or impossible?"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by agashka on 2007-06-18
Hi, first, i know this have been asked a billionth of time. Ive actually googled alot about this problem.

Im running with a dell 22" lcd, and 1024x768 is not what id like. 1680x1050 is more what id want. Ive tried MANY ways to get to that resolution, reconfiguring xserver-xorg over 10 times, editing xorg.conf at least 50 times. Doesnt work. When i boot, X just shows me an error each time i modify the xorg.conf 'failed to start the X server' (then i hit reconfigure xserver-xorg and set to vesa and configure the whole thing)

this is my first try to installing linux. Been 2h just to configure a damn resolution. I cant imagine how time gonna get me setted up >.<
anyway here my current xorg.conf

plz help, and thx

---

### Post by luvr on 2007-06-18
1680x1050 should be possible--I'm running at that very resolution on a Dell Latitude D820 laptop.

There doesn't seem to be anything wrong with your xorg.conf file either, except that you're using the **vesa** driver--I'm not sure if that will support the resolution you're aiming at.

I'd suggest you enable the **nvidia** driver instead. While it's a proprietary, binary-only, module, it may well solve your issue. Just open the Restricted Drivers Manager (*"System"* --> *"Administration"* --> *"Restricted Drivers Manager"*), enter your password when prompted, and tick the checkbox to enable the **NVIDIA accelerated graphics driver.**

If you prefer to use only open-source modules, then you could use the **nv** module instead; edit your xorg.conf file, and replace the *vesa* driver with *nv.*

---

### Post by sloggerkhan on 2007-06-18
I'd try adding a modeline for your monitor. 

try using 
```

$gtf 1680 1050 [refresh rate]

```

Should looks something like:
```

$ gtf 1680 1050 60
  # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

namer@comp:~$ 

```

Then add the modline to the monitor section of the xorg.conf as follows:
```

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 84.0
	VertRefresh  43.0 - 65.0
	ModeLine     "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  #replace this with your modeline from the gtf command
	Option	    "DPMS"
EndSection

```

If all goes well, that resolution should become reachable.

You may also try the xrandr command to see what your comp thinks is supported.

---

### Post by agashka on 2007-06-18
everytime i add something to the damn xorg.conf it screws up, now i got it working with reconfigure and putting NV instead of vesa, thanks sooo much!

---

### Post by nutz on 2007-06-18
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Monitor		"Generic Monitor"
	DefaultDepth    24
	Option         "metamodes" "CRT: 1680x1050_60_0 +0+0"
	SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

---

### Post by sloggerkhan on 2007-06-18
Oh, you were using vesa lol... I didn't notice. Vesa is a fairly limited CPU driven graphics driver usually used for fallback.
It really sucks for the most part, but is pretty much guaranteed to work on any system.

---

