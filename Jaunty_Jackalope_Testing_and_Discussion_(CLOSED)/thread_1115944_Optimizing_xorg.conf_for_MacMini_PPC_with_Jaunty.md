---
title: "Optimizing xorg.conf for MacMini PPC with Jaunty"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by JohnFante on 2009-04-04
I have a PPC MacMini with the standard Radeon 9200 chip. I am not sure that the auto generated xorg.conf is optimized as best as possible to get the most out of my setup. 

My xorg.conf looks like this right now.

```
Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
	Driver		"ati"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I have inserted the Driver "ati" line in the "Device" section (googled my way to that one) in the hope of getting just a little bit 3D support but it hasn't made any difference. 

Any suggestions?

Thank you in advance!

---

### Post by JohnFante on 2009-04-07
Bump :-)

---

