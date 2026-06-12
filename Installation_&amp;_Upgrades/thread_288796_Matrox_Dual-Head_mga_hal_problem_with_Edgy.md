---
title: "Matrox Dual-Head mga_hal problem with Edgy"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by itsterry on 2006-10-30
Have recently upgraded to Edgy from Dapper, and discovered that I can't get two monitors working at once on my Matrox G400 Dual-Head

Although I can get my Dual-Head working on ONE monitor using the fix from the excellent pjssilva at [http://www.ubuntuforums.org/showthread.php?t=286199](http://www.ubuntuforums.org/showthread.php?t=286199), 
Dual-Head support requires the mga_hal library from matrox.

I've found a patch for the standard Edgy deb package that puts in mga_hal before recompiling, BUT the standard Edgy deb contains a bug which leaves the screen blank (hence the fix from pjssilva above)

So can anyone tell me how to put the mga_hal into a pjssilva-type fix so I can get my dual-head working again ?

Fwiw, here's the relevant output from /var/log/Xorg.0.log:
(heavily snipped)

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux portal 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 30 14:08:52 2006
(==) Using config file: "/etc/X11/xorg.conf"


(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules/libvgahw.so
(--) MGA(1): Chipset: "mgag400" (G400)
(EE) MGA(1): This card requires the "mga_hal" module for dual-head operation
	It can be found at the Matrox web site <http://www.matrox.com>
(II) UnloadModule: "mga"
(II) UnloadModule: "vgahw"


All feedback very much appreciated...

---

### Post by pjssilva on 2006-10-30
Where did you get the patch? Is it easy to apply?

Hopefully I can apply it to the Debian unstable driver I compiled and then recompile. If I succeed, I can post the non-free driver in my website for download.

Give me as much information as you can. 

Paulo

Obs: I may not be able to do that work tomorrow, but I may find time to try it soon.

---

