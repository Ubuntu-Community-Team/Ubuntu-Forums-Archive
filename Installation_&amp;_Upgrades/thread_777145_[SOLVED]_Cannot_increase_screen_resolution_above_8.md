---
title: "[SOLVED] Cannot increase screen resolution above 800x600 in 8.04"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by seoras on 2008-05-01
I have installed 8.04 on and old PC but the maximum screen resolution offered is 800x600. 

**System>Preferences>Screen Resolution** does nothing.

Then go to **usr/share/applications/Screens&Graphics** select my monitor model from the list, set the screen resolution to 1024x768 then select the graphics card from the list ATI Rage Pro (old). I am then informed to log off for changes to take effect, which I do. System then reports running in low graphics mode and suggests configuring, which I do, as before selecting the graphics card and monitor and setting the resolution to 1024x768.

Then the system boots to an 800x600 screen, so the configuration has no effect.

I have installed 7.10 on machines with the exact same specification with no problems at all, so if there isn't a solution I'll go back to 7.10.

---

### Post by mixmaster on 2008-05-01
Have you tried moving the xorg.conf file from the 7.10 machine to the 8.04?  I had to do this to get any graphics at all on my ThinkCentre desktop (integrated Intel graphics).

---

### Post by SnakeHips on 2008-05-01
just incase it's a permissions' thing try this.

```
gksudo displayconfig-gtk
```

---

### Post by seoras on 2008-05-01
Thanks for the suggestions guys but on this occasion I managed to solve the problem by using a different monitor and re-installing Ubuntu 8.04. Now I have the whole range of resolutions available.

There must have been some weird problem between the monitor and the graphics card?

---

### Post by Lantesh on 2008-05-01
I've had this issue in the past, but with Gutsy, not Hardy.  The way I fixed it was to uninstall the restricted driver I was using, and reinstall reinstall it using Envy.

---

### Post by odin79 on 2008-05-01
In your /etc/X11/xorg.conf file you should have a section like this:

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Primary)"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

The subsection "display" defines the resolutions available. My guess is that you only had "800x600" there after the upgrade.

---

