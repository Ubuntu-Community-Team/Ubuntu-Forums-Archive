---
title: "XWindows doesn't start - monitor description includes quote charater"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by foxylad on 2005-02-02
I've already solved this one, but am noting it here so others can find it.

After the Warty Warthog install, XWindows would not start up. The problem turned out to be that my monitor describes itself as **CMC 17" AD** , and when the /etc/X11/XF86Config-4 file is configured, you end up with a section like this:

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9000 Pro (RV250 If)"
	Monitor		"CMC 17" AD"
	...

That extra quote character stops X from reading the file. To fix it:

sudo vi /etc/X11/XF86Config-4

/Monitor
*arrow key across to hightlight the extra quote* 
x
ZZ

Then reboot, and enjoy this fine distribution!

Cheers!
Greg.

---

### Post by foxylad on 2005-02-02
Just found out this is already fixed in Hoary Hedgehog. And Microsoft have the gaul to say their support is better... yeah right!

---

