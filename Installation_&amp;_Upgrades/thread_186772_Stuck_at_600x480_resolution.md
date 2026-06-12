---
title: "Stuck at 600x480 resolution"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by BaffledMollusc on 2006-06-02
This is weird.

During and after installation, screen resolution is stuck at 600x480. If I go to the  resolution changing option in the menu, that's the only resolution available. Futhermore, the only refresh rate available is -19579Hz.

When I go to check the xorg.conf file, I see that there are loads of resolutions available, but they're not showing up in the resolution changing menu. The relevant sections of my xorg.conf file are copied at the end of this post.

I'm a bit disturbed by the monitor settings, since I have an LCD monitor, which is working on a DVI output. So why are there refresh settings at all? What does DPMS mean?

I've tried running "sudo dpkg-reconfigure xserver-xorg" but that doesn't help.

Any suggestions?

Section "Device"
	Identifier	"ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by JSchwage on 2006-06-02
I've gotten stuck in 640x480 before. It can happen if you forget to turn your monitor on when Ubuntu is booting up. But I'm getting the impression that you've probably already tried restarting your computer.

---

### Post by BaffledMollusc on 2006-06-02
[QUOTE=JSchwage]I've gotten stuck in 640x480 before. It can happen if you forget to turn your monitor on when Ubuntu is booting up. But I'm getting the impression that you've probably already tried restarting your computer.[/QUOTE]
Yep, I've alread tried that :)

The odd thing is that Ubuntu 5.10 detected exactly the same hardware setup fine, and didn't have any resolution problems.

Edit: In case it matters, I'm using the AMD64 version.

---

### Post by BaffledMollusc on 2006-06-02
Okay, I solved it by installing the proprietory fglrx ATI driver. The resolutions work now, although I don't think it should be necessary to install binary drivers to do this.

The other odd thing is that now I only have refresh rates of 47Hz and 43Hz available. Considering that I'm using an LCD, I have no idea what this means.

Oh, well, at least I have a decent resolution now.

---

