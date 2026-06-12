---
title: "&quot;Disable&quot; is not a valid keyword in this section."
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by viniciuscarvalho on 2009-10-14
Hello there! After using envyng to fix a problem with memory leaking using catalyst drivers for my ATI 4650. I now get the following message when running amdcccle:

Parse error on line 12 of section Module in file xorg.conf
	"Disable" is not a valid keyword in this section.
Parse error on line 12 of section Module in file xorg.conf
	"Disable" is not a valid keyword in this section.


Well, I've opened the xorg.conf and removed the problematic line:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2048 2048
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection


restarted the system, and the error message persists. Anywhere else I should be looking at?

Regards

---

### Post by viniciuscarvalho on 2009-10-16
I still can not get amdcccle working. I looked everywhere and did not find where It might be loading a xorg.conf file that may have the Disable keyword.

Anyone please?

---

