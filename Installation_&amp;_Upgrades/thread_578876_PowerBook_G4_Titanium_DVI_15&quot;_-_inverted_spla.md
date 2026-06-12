---
title: "PowerBook G4 Titanium DVI 15&quot; - inverted splash - black screen - no CLI"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by mtoriello on 2007-10-17
I'm having some trouble trying to boot ubuntu from the "desktop" cd.  I've tried both 6.06.1 and 7.04 versions of ubuntu and get the same results.

The following is a description of the mac laptop that I am trying to install ubuntu on and what happens when I try to install it.



PowerBook G4 Titanium DVI 15" laptop (A1025)

Hardware Overview:
  Machine Name:	PowerBook G4 15"
  Machine Model:	PowerBook3,5
  CPU Type:	PowerPC G4  (3.3)
  Number Of CPUs:	1
  CPU Speed:	1 GHz
  L2 Cache (per CPU):	256 KB
  L3 Cache (per CPU):	1 MB
  Memory:	1 GB
  Bus Speed:	133 MHz
  Boot ROM Version:	4.5.3f2


From what I could find online I think that the graphics card is an 
ATI Mobility Radeon 9000, and that it is connected to (soldered) to the logic card.
  
Graphics/Displays:
  Chipset Model:	ATY,RV250M9
  Type:	Display
  Bus:	AGP
  VRAM (Total):	64 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x4c66
  Revision ID:	0x0002
  ROM Revision:	113-xxxxx-106
  Displays:
Color LCD:
  Display Type:	LCD
  Resolution:	1280 x 854
  Depth:	32-bit Color
  Built-In:	Yes
  Core Image:	Not Supported
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
Display:
  Status:	No display connected
  
  
  
  
At the "boot:" prompt:

Here are the variable values displayed when I type "help" at the "boot:" prompt:
device=/pci@f2000000/mac-io@17/ata-3@20000/disk@0
partition=2



"live" boot:

- screen turns black with two white segmented bars, one in the middle and one at the bottom
- while this is happening it still sounds like the live version is installing properly


"live video=ofonly" boot:

- text loading output scrolls up the screen:
	loading kernel
		Elf32 lernel loaded
	loading ramdisk
	...
- screen flashes white and then black
- the splash logo pops up drawn with inverted, possibly 8bit color scheme
	- all of the splash screen scrolling load steps show up as [OK]
- screen goes to black with a blinking cursor in the upper left
	- text loading options scroll up the screen:
		INIT: version 2.86 booting
		...
		starting GNOME desktop manager
- screen turns black but not an illuminated black a dark black as if there were no signal running through the lcd anymore, Similar to when the mac laptop goes into sleep mode.
- the cd is still doing stuff
- then I hear the startup audio (chimes)
- then the cd player goes into passive spin mode

- at this point I try to do a ctl-opt-F1 to get to a terminal, when I do this the screen fades/bleeds to white with some black lines across it.



Roughly the same thing happens when I try to "boot:" in the other modes:
- live-nosplash video=ofonly
- live-powerpc video=ofonly
- live-nosplash-powerpc video=ofonly

---

