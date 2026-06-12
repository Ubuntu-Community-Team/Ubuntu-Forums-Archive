---
title: "Nvidia"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by TomBull on 2007-06-16
I just installed Ubuntu 7.4 and ran automatix.
Automatix installed nvidia drivers but now my screen resolution is wrong and I cannot change it in menu preferences.
How do I correct this.

---

### Post by benerivo on 2007-06-16
I think I know what your problem is. To have Ubuntu use a resolution that is not listed, I would edit the /etc/X11/xorg.conf file. Towards the bottom of this file will be a list of resolutions that will be used for the display. You may  just need to add a new resolution at the start, so  instead of looking like this...
		Modes		"1024x768"	"800x600"	"640x480"

it looks like this...
		Modes		"1152x864"     "1024x768"      "800x600"	"640x480"

---

### Post by TomBull on 2007-06-16
Thanks, that seems to have done the trick.

---

