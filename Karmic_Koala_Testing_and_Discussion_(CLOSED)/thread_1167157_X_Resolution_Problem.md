---
title: "X Resolution Problem"
date: 2009-05-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fifth on 2009-05-22
I'm stuck on 800x600 after todays updates :(

I've tried using using my xorg.conf's from before the 'Configured Device' era, but doesn't seem to fix the problem - just introduces random lockups.

[edit]
Not sure what I was doing wrong in my xorg.conf, but its working now :D
[/edit]

---

### Post by fifth on 2009-05-22
Just me then :(

Anyway, to add extra info, I'm on Intel 945GM Express. Anyone else having probs? or should I wipe n re-install?

---

### Post by thonuz on 2009-05-22
Me too. I am playing around with it at the moment. i945 on vaio with busted hard drive.

---

### Post by lalitgaur on 2009-05-22
I am getting this problem too

---

### Post by bzarnsy on 2009-05-22
same here. when i saw intel driver in the updates list i thought maybe
it finally got fixed but i guess it didn't. 640 X 480 just doesn't look
look right on my 19 inch wide screen.

---

### Post by Stephmau on 2009-05-23
Same here on intel 945GME with the last update, Asus 1000he

---

### Post by fifth on 2009-05-23
Glad I'm not alone, i'm tempted to go for the ppa drivers but would rather keep this a clean Karmic install, just have to wait it out and hope for a fixed update :D

---

### Post by yellerKat on 2009-05-23
Me too on my ancient Fujitsu-Siemens.

---

### Post by fifth on 2009-05-23
I've managed to get full resolution and effects back now :D

It looks like the intel driver was not being loaded, the vesa fallback driver was being used.

I've changed my xorg.conf to;

```

# xorg.conf to specify intel driver 23/05/2009

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection



```

All working properly now by working around the problem, but still not sure what the actual problem is :/

---

### Post by meeples on 2009-05-23
> **fifth said:**
> I've managed to get full resolution and effects back now :D

It looks like the intel driver was not being loaded, the vesa fallback driver was being used.

I've changed my xorg.conf to;

```

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

All working properly now by working around the problem, but still not sure what the actual problem is :/


thanks for that, i just copy and pasted that into xorg.conf, and hurrah problem solved :D:D

thanks again :D

---

### Post by yellerKat on 2009-05-23
> **fifth said:**
> 
All working properly now by working around the problem, but still not sure what the actual problem is :/

Thank you, my eyes were popping! :???:

---

### Post by Hershey on 2009-05-23
Same issue here with a 1000H.  I'm guessing the issue stems from this change:

> 
xserver-xorg-video-intel (2:2.7.1-1) unstable; urgency=low

  [ Brice Goglin ]
  * New upstream release.
  * Install the upstream NEWS file, closes: #524334, #524336.
  * Move the -dbg package to section debug.

  [ David Nusinow ]
  [b]* Remove 01_gen_pci_ids.diff. The X server now uses an internal table to
    choose a driver during autoconfiguration.[/b]
    + Disable patch system and remove quilt from build-deps.


From my Xorg log:
> 
(--) PCI:*(0@0:2:0) Intel Corporation Mobile 945GME Express Integrated Graphics Controller rev 3, Mem @ 0xf7f00000/524288, 0xd0000000/268435456, 0xf7ec0000/262144, I/O @ 0x0000dc00/8

...

(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) No matches found for this device in /usr/share/xserver-xorg/pci
(==) Registering 'vesa' as fallback
(==) Matched vesa for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "vesa"


So whatever was in 01_gen_pci_ids.diff needs merged into Xserver's look up table?

---

### Post by Hershey on 2009-05-23
I took the intel.ids from xserver-xorg-video-intel_2.7.0-1ubuntu1_i386.deb and placed it in /usr/share/xserver-xorg/pci.  Rebooted and Xorg picked the intel driver instead of VESA.

> 
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.7.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, IGD_GM, IGD_G, 965G, G35,
	965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0


---

### Post by psyke83 on 2009-05-23
> **Hershey said:**
> I took the intel.ids from xserver-xorg-video-intel_2.7.0-1ubuntu1_i386.deb and placed it in /usr/share/xserver-xorg/pci.  Rebooted and Xorg picked the intel driver instead of VESA.

Well, a simpler way to fix this until the problem is fixed officially is to manually specify the "intel" driver in the Device section of your xorg.conf. I also notice that the Synaptics driver isn't detected by default for my laptop, either.

---

### Post by bzarnsy on 2009-05-23
i just tried this intel.ids thing and it works fine now.

---

### Post by doomsword2001 on 2009-05-23
worked for me aswell, thx
:popcorn:

---

### Post by psyke83 on 2009-05-23
This should be fixed with the latest xorg-server upload.

[https://lists.ubuntu.com/archives/karmic-changes/2009-May/001550.html](https://lists.ubuntu.com/archives/karmic-changes/2009-May/001550.html)

---

### Post by Hershey on 2009-05-24
> **psyke83 said:**
> This should be fixed with the latest xorg-server upload.

[https://lists.ubuntu.com/archives/karmic-changes/2009-May/001550.html](https://lists.ubuntu.com/archives/karmic-changes/2009-May/001550.html)

Updated, removed intel.ids, rebooted, and the intel driver was successfully chosen for me.

---

