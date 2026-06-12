---
title: "Resolution issue with X (xorg.conf won't help..)"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by m@ra on 2007-05-11
Hi All,

I've been few days struggling with my new computer. It has MSI motherboard with builtin GPU and also Radeon 7100 GS. I can get  everything else working except 1280*1024 resolution. I've set some stuff already at xorg.conf with and without GUI. And I have installed latest Nvidia drivers.


Screen is LG1715S. Ubuntu release 7.04 tested also with 6.10 => no luck. Screen used to work fine with 1280*1024 in my old computer.

Check info below for details.

----

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation GeForce 7100 GS"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280*1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

-----

I receive error from xonf gui editor

---

(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7100 GS at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.02.33.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7100 GS at PCI:3:0:0:
(--) NVIDIA(0):     LG L1715S (CRT-0)
(--) NVIDIA(0): LG L1715S (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280*1024"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (76, 72); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option

---

mara@mabuntu:~$ sudo apt-get install nvidia-glx
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx is already the newest version.
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-xext-dev x11proto-kb-dev libglib1.2-dev
  libxi-dev libxdmcp-dev xtrans-dev x11proto-core-dev libssl-dev libxext-dev
  zlib1g-dev x11proto-input-dev libxau-dev libgtk1.2-dev libx11-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mara@mabuntu:~$

---

### Post by Ken_Lewis81 on 2007-05-11
Add "1280**x**1024" to each line: ```
Modes "1024x768" "800x600" "640x480"
```

You need an x, not a *.  You may also need to change VertRefresh so it reads 43-85.

Hope that helps.
Take care.
Ken.

---

### Post by m@ra on 2007-05-11
Hi Ken,

Thanks - it was just a typo. Don't know why it didn't detect it in the first place that resolution!

Regards,

-markus

---

### Post by Ken_Lewis81 on 2007-05-16
It didn't get it right because it expects **exactly** the right thing in the configuration file.  The computer's just a very big mathematics machine, so has to have things logical: either right or wrong.  Unfortunately a typo is wrong.

Take care.
Ken.

---

### Post by larryh on 2007-06-22
I'm having a similar problem with my XFX GeForce 7100 GS in that I can't change to any other display other than 640x480 (using the nVidia proprietary driver on Feisty).  I read the man page for xorg.conf and I think I know what I'm missing but not the syntax that needs to be there.  My conf file looks a little different than that posted above:

--snip--

Section "Monitor"
  identifier "MultiSync 95"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection

Section "Device"
  identifier "nVidia Corporation GeForce 7100 GS"
  boardname "NVIDIA GeForce 7 Series"
  busid "PCI:1:0:0"
  driver "nvidia"
  screen 0
  vendorname "NVIDIA"
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "nVidia Corporation GeForce 7100 GS"
  Monitor "MultiSync 95"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 640 480
    modes "640x480@60"
  EndSubSection
EndSection

--snip--

So I think I need to add "1024x768@60" to the modes under Screen and add another modeline under Monitor but its the syntax of the modeline that I'm unable to figure out since I'm a little shaky on what values to use.  I'm assuming:

modeline "1024x768@60" xx.x 1024 xxx xxx xxx 768 xxx xxx xxx -vsync -hsync

but even if I'm on the right track I'm unsure about the xxx's.  Also how do I determine what to put for even higher resolution lines and widescreen outputs for when I eventually hook it up to my bigscreen TV?

---

