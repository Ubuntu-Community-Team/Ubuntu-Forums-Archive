---
title: "Upgrade to 7.10 Gusty, ATI card won't work with xgl"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by chaos2286 on 2007-10-21
Hey,

I've recently upgraded to Gusty Gibbon to use those sweet desktop effects.  However, whenever I log in with xgl enabled everything is slow and unresponsive.  I've created a touch disable to stop it from working for now.  I'd really like to get it working though, so if anyone can help me I'd be so thankful.  Heres my info.

Graphics Card:  ATI Radeon 9800 Pro

In xorg.conf:

Section "Extensions"
	Option		"Composite"	"1"
EndSection

Whenever I try to enable the desktop effects it just clearly states "cannot enable desktop effects".
I'm going to post what compiz says once I re-enable xgl for that purpose.

Thank you !
- Chaos

---

### Post by chaos2286 on 2007-10-21
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :2.0

---

### Post by Applegeek on 2007-12-20
Did you ever get this resolved?  Are Radeons useless for Linux?

---

### Post by Mark Phelps on 2007-12-20
Radeons (at least some of them) are fine for Linux.

If you want help with video problems, would be better to go to the Multimedia and Video forum.  There are LOTS of posts there, including How-to's on fixing ATI-related video problems.

---

