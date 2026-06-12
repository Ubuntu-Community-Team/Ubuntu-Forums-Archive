---
title: "[SOLVED] Savage (X11) driver b0rked?"
date: 2008-12-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by knarf on 2008-12-27
Is anyone else out there seeing (or rather not seeing...) problems with recent savage_drv.so versions? On my venerable Thinkpad T23 X does not want to run anymore as the savage driver (usr/lib/xorg/modules/drivers/savage_drv.so) and the dri driver (/usr/lib/xorg/modules/extensions/libdri.so) seem to dislike eachother - see also [bug 311544]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/311544")...

---

### Post by knarf on 2008-12-28
Hm, I must either be the only Savage user (no pun intended) or the only one having problems...

---

### Post by Gina on 2008-12-28
I think the graphics on one of my old desktops is Savage - will have to check when I can.  It's not in commission ATM.

---

### Post by knarf on 2008-12-28
If you find the time to do so, please do. As you can glean from the bug report I've already run past a compiler optimization 'bug' into a bunch of undefined values which really should be defined. Debugging X is not really my favourite way of spending the last few hours of the day...

---

### Post by linux6994 on 2008-12-29
I saw this under the thread x-Server breakage, I have not tried to go back up to Juanty since it screwed my Savage driver.

---

### Post by knarf on 2008-12-29
I made a small patch which fixes this segfault - the savage driver now works as good/bad as it did before the server upgrade. The patch is attached to the [bug report (#311544)]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/311544"). To build a package using this patch you'd want to:


[LIST=1]
[*]copy the patch to the debian/patches directory in the unpacked package source tree
[*]regenerate the patch series file by doing something like ```
(cd debian/patches && rm series && ls > series)
```
[*]rebuild the package by issuing ```
fakeroot dpkg-buildpackage -b
``` (this just builds the binary package)
[/LIST]
I can provide a binary package for i386 if this sounds like gibberish. I have not attached it to the bug report as I don't think launchpad is the place to do that, nor do I want to encourage you to download binary packages from untrusted sources. Maybe Tormod Volden can add the patch to his PPA?

---

### Post by ShirishAg75 on 2008-12-30
perhaps you can post a pm/email tromod volden and give a link to the thread here as well as attach your patches and sign them off. 

just my 2 paise.

---

### Post by knarf on 2008-12-30
He already knows, as do the savage maintainers (got a reply from Timo Aaltonen). I'll send the patch upstream as well.

---

