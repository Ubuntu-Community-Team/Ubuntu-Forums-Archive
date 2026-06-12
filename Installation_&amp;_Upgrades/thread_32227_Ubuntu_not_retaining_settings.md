---
title: "Ubuntu not retaining settings"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by GreatSunJester on 2005-05-06
Just installed Hoary on an old (VAIO - P2 400, 10 gig drive, G200 video)... complete format and install.

Ubuntu runs fine on it, though I need to add some ram I think.   My problem is the settings.
Every time I boot the machine up, I have to reset the screen res to where I want  (defaulting to 1280 and 60Hz) and re-configure the network (it picks up an IP from my router, but assigns the router IP as the first DNS and uses a search domain I have never heard of) 

Has anyone else encountered this?

---

### Post by Xian on 2005-05-06
[QUOTE=GreatSunJester]
Every time I boot the machine up, I have to reset the screen res to where I want  (defaulting to 1280 and 60Hz)....[/QUOTE]
What have you set in the /etc/X11/xorg.conf "Screen" and "Monitor" sections? You'd want something like this in the Screen portion (replace the leading resolution with what you desire):

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"<your type here>"
	Monitor		"<your brand here>"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
</snip>
```

The "Monitor" section would need to correspond to the manufacturer specs. Mine looks like this:

```
Section "Monitor"
	Identifier	"COMPAQ 7500"
	Option		"DPMS"
        HorizSync       30-70
        VertRefresh     50-140
EndSection
```

---

### Post by GreatSunJester on 2005-05-06
Will have to check after the new install is done (grabbed Kubuntu).   I would guess (could be my mistake right there!) that the monitor section is OK, as I can select 1024x768 with 85Hz and switch to it.  My main concern was the system was not retaining any settings after reboot.

Dropping in 512 meg ram instead of the 64 that was in there.....spare parts!

EDIT:
LOL -- maybe the problem was all mine.  Staring at a screen right now during the setup telling me hda: drive not ready for command.
Looks like a harware failure was hitting me.  Good thing I have a few other drives laying about.

---

### Post by GreatSunJester on 2005-05-09
Old Sony VAIO up and running Kubuntu now -- running quite well I must say.  Used the GUI screen control planel and set the desktop to 1024x768 85Hz -- it retains the settings after reboots.

Network still does not want to though -- defaults the DNS to 192.168.0.1 and my normal primary DNS as the secondary.  Konqueror works fine but Firefox seems to have a hard time with these settings.  Ah well -- playing with Kubuntu.

Install Synaptic -- such a treasure compared to the KDE version.

EDIT:  and I see there are some helpful posts in the Kubuntu forum that may fix this problem for me tonight!

---

