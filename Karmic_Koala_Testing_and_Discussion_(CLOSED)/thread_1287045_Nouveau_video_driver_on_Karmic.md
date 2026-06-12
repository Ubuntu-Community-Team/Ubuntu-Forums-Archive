---
title: "Nouveau video driver on Karmic"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by benjo316 on 2009-10-09
I've tried installing xserver-xorg-video-nouveau on my laptop (a Dell Inspiron 8100 with GeForce2 Go graphics), and it seems to finish successfully... however, when I boot, I see the splash, it fades away (like it should, I think), but nothing else happens (the system is silent, except for those weird sounds that the system always makes). If I press the power button, the splash fades back in, then out again after a while and the system locks up.

I didn't see any logs, so I'll experiment a little more and bring what I find later.

In the mean time, is this a known issue? Am I doing something bad in my xorg.conf(below)?

Any help/advice would be appreciated. ^.^

xorg.conf:```
Section "Device"
	Identifier	"nVidia Corporation NV11 [GeForce2 Go] (rev b2)"
	Driver		"nouveau"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
	  Depth		24
	  Virtual	1400 1280
	EndSubSection
	Device		"nVidia Corporation NV11 [GeForce2 Go] (rev b2)"
EndSection
```Note: If "Device" and "Identifier" don't match, it's because I typed them by hand. They match in the config file.

---

### Post by mikewhatever on 2009-10-09
I think the following explains what happened well:

[http://packages.ubuntu.com/karmic/xserver-xorg-video-nouveau](http://packages.ubuntu.com/karmic/xserver-xorg-video-nouveau)

> Note that these drivers are INCOMPLETE, and are only really useful for testing at this point. People needing a stable driver should use the "nv" driver instead. Although the upstream nouveau drivers provide some 3D support, these packages do not include the necessary files. Users requiring 3D support should use the non-free "nvidia" driver.



---

### Post by benjo316 on 2009-10-09
Thanks for the reply.

I knew they were incomplete, but I've had better experience with them(err, it?) and according to the [feature matrix]("http://nouveau.freedesktop.org/wiki/FeatureMatrix"), 2D is (basically) done. I, of course, don't expect anything 3D at this point.

And since the splash screen is actually displayed, I figure the most likely thing to be causing the problem (KMS) probably isn't.

Which is why I'm here. :)

Of course, if anyone thinks this belongs somewhere else (like a bug on launchpad, or similar), I'd be glad to report it. I just wanted to be sure it wasn't a configuration problem on my part before I jumped to that.

---

### Post by CHaoSlayeR on 2009-10-27
I'm running nouveau on my Dell Inspiron 8600 with a GeForce FX Go5200 with an external display attached and it just works fine.

Although I must say that I'm still on Jaunty and as I see most of the bug reports in the last months dealed with KMS issues I think deactivating KMS might be the best way to get a working setup for now.

For the reference I leave my xorg.conf here:
```
Section "ServerLayout"
	Identifier     "DualHead Layout"
	Screen      0  "primary screen" 0 0
EndSection

Section "Device"
	Identifier     "nVidia GeForce FX 5200 GO 64M"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce FX Go5200"
	BusID          "PCI:1:0:0"
	Driver         "nouveau"
	Option         "AccelMethod" "EXA"
	Option         "monitor-LVDS-0" "primary"
	Option         "monitor-VGA-0" "secondary"
	Option         "MigrationHeuristic" "greedy"
	Option         "FPScale" "false"
	Option         "ScalingMode" "noscale"
EndSection

Section "Monitor"
	Identifier     "primary"
	VendorName     "Dell"
	ModelName      "LGP"
	HorizSync       30.0 - 75.0
	VertRefresh     60.0
	Option         "Position" "1600 400"
	Option         "PreferredMode" "1280x800"
EndSection

Section "Monitor"
	Identifier     "secondary"
	VendorName     "NEC"
	ModelName      "Multisync FE1250+"
	HorizSync       30.0 - 110.0
	VertRefresh     50.0 - 160.0
	Option         "LeftOf" "primary"
	Option         "Position" "0 0"
	Option         "PreferredMode" "1600x1200"
EndSection

Section "Screen"
	Identifier     "primary screen"
	Device         "nVidia GeForce FX 5200 GO 64M"
	Monitor        "primary"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Virtual    2880 1200
	EndSubSection
EndSection

Section "DRI"
	Mode           0666
EndSection

```

Also you might have a look inside the bugs over at [bugs.freedesktop.org]("http://bugs.freedesktop.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&product=xorg&component=Driver%2Fnouveau&long_desc_type=substring&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=allwords&keywords=&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailqa_contact2=1&emailcc2=1&emailtype2=substring&email2=&bugidtype=include&bug_id=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Importance&field0-0-0=noop&type0-0-0=noop&value0-0-0=") if there is anything that matches your situation.

Regards,

C]-[aoZ

---

