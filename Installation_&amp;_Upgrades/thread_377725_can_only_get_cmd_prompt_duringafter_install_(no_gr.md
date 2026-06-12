---
title: "can only get cmd prompt during/after install (no graphics)"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by tctimmeh on 2007-03-06
I'm trying to install kubuntu edgy and can't seem to get anything "graphical" working.  Here's what I typically encounter:

I boot from the cd and get a menu with "Start/Install kubuntu", "install oem", ... etc. which seems right.  If I choose Start/Install, it loads the kernel and does whatever it needs to do and then drops me straight to a linux cmd prompt with no error messages or anything.

So that's not at all what I was expecting after choosing "Start kubuntu" so I decided to go ahead and just do an install.  The install goes fairly smoothly (very similar to installing debian, naturally).  Then I reboot, choose linux-generic from the grub boot menu, and watch the disaster.  It bitches about not being able to connect to the x server at localhost:0 then drops me to a login prompt.

Now... one interesting thing to note: This is how far I get when I change my screen resolution to 1280x1024 in the very first menu when booting from the dvd.  If I leave it at 640x480 I don't even get this far.  After installation and reboot it gets about half way through the progress bar while loading and then a bunch of green lines appear on my screen and I need to reset.

My hardware highlights are:
MSI MS-7125 mobo /w nvidia nforce2
AMD Athlon64 3500+
ATI Radeon x850
sound, networking, everything else, is all on-board

I should also note that I've tried both the i386 and the amd64 dvd with no luck.  This is intended to be a dual boot setup with an existing winXP installation.

I'm not a complete linux newb but I haven't had the time/patience to dig into this, and I'm not familiar with configuring X at all.    If anybody can suggest something to try I'd really appreciate it.

---

### Post by teaker1s on 2007-03-06
at grub select recovery kernel and when you get text login-login

```
sudo dpkg-reconfigure xserver-xorg
```

for to get basic screen choose "vesa" as driver and work through graphical choices

my mistake I saw nvidia on list and missed ati, my appologies and Taurus is correct

---

### Post by taurus on 2007-03-06
Log in with your username and password.  Then at the prompt, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```
Pick **vesa** as the driver for your graphic card and see if X is running again with

```
startx
```
Otherwise, reboot.

---

### Post by tctimmeh on 2007-03-06
Thanks for the replies.  I tried reconfiguring X and got a little further.  The with the vesa driver selected my HD grinds like it's doing something but my monitor gets no signal.  

So I booted into the recovery console and switched the device driver back to "ati" in xorg.conf and did 'startx' which got me the following errors:

```
[EE] No Devices Detected
Fatal Server Error:
no screens found
```

Of course my xorg.conf seems to me to contain valid device and screen sections:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X850 Pro (R480)"
	Driver		"vesa"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"VX924"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X850 Pro (R480)"
	Monitor		"VX924"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

---

### Post by taurus on 2007-03-06
Is your graphic really located at that?

```
BusID		"PCI:5:0:0"
```

What's the output of this command from a prompt?

```
lspci
```

---

### Post by tctimmeh on 2007-03-07
lspci has the following, which looks correct:

```
05:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)]
05:00.1 Display controller: ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)] (Secondary)
```

but there's two, so is the problem that it's trying to start on the wrong monitor of my dual-head card?  I'm not sure I'm interpretting this correctly.  The way I'm running right now is that my video card has an analog and dvi out and I'm running off the dvi.  I tried setting the BusID to 5:0:1 in my xorg.conf but then startx spits out:

```
(WW) VESA: No matching Device section for instance (BusID PCI:5:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found

```

---

### Post by taurus on 2007-03-07
Is "05:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)]" an onboard graphic controller card?  If it is, try to turn it off in the BIOS.  Then, boot into recovery mode from GRUB menu and reconfigure X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by tctimmeh on 2007-03-07
No, I have no onboard video.  If I'm interpretting lspci correctly then 5:0.0 and 5:0.1 are different functions of the same device (which would be the affore-mentioned radeon x850).

I just tried out the flgrx drivers which got X starting, but only up to the menu where it wants me to configure a new user.  Then the screen goes black and the monitor gets no signal again.  Reboot doesn't help; same result.

---

### Post by I'm_pissed on 2007-03-08
If I'm not mistake, PCI Express is completely different from PCI, and the bus location would be different too, as well as the way you specify it in the xorg.conf. I'm not sure how you would write it in the config file, but I bet that it is causing the x server to look at your regular PCI bus or something

---

### Post by tctimmeh on 2007-03-09
I've finally got some success!  :)

I found on [this page]("http://wiki.cchtml.com/index.php/Troubleshooting") that my combination of 64bit + radeon x800 + DVI output is a deadly combination.

I'm now running with the 32bit kubuntu on the vesa drivers, which is horribly slow but at least I'm running.

---

