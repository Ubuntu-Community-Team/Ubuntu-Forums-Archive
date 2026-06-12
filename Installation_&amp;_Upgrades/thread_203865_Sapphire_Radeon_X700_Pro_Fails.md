---
title: "Sapphire Radeon X700 Pro Fails"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by tomazos on 2006-06-26
Upon booting from the Live/Install CD of Dapper 6.06 the installation fails to start X, with an error message of "no screens found".

[The Xorg.0.log file]("http://www.tomazos.com/Xorg.0.log.txt")

[The xorg.conf file]("http://www.tomazos.com/xorg.conf.txt")

[The dmesg file]("http://www.tomazos.com/dmesg.txt")

The graphics card is a *Sapphire Radeon X700 Pro 256MB*.

I have tried it with two different monitors.

I have tried dpkg-reconfigure xserver-xorg, and setting my display adapter to VESA.  This will successfully launch X.

Clearly the problem is with the "ati" driver. (?)

The interesting part from the xorg.conf is:

[FONT="Courier New"]Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X700 Pro (RV410)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection[/FONT]

lspci tells me that the graphics card is on 0000:01:00.0 (Primary) and 0000:01:00.1 (Secondary) - which seems to match "PCI:1:0:0" right?

The interesting bit in the Xorg.0.log file is:

[FONT="Courier New"](II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon X700 Pro (RV410)".
(WW) ATI:  PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 1:0:1 could not be detected!
(EE) No devices detected.[/FONT]

Any ideas why the ATI driver is failing?  Where is the appropriate place to report this?  Is there anyway to get more verbose debugging information as it tries to load the ATI driver?  Is it definately the ATI driver from the above logs?

Thanks,
Andrew.

---

### Post by scxtt on 2006-06-26
you should give fglrx drivers a go ... check the link in my sig, works great for my X800 ...

---

