---
title: "[SOLVED] X won't start after upgrade"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by dcroxton on 2007-10-20
I upgraded to Gutsy about 2 weeks ago and have been using it successfully since, but today, all of a sudden, X won't start for me.  I tried dpkg-reconfigure xserver-xorg, but it didn't help.  I use a dual monitor setup, so I switched to a single monitor xorg.conf, and that didn't work either.  Here is the output I get when I run "startx":

xauth:  creating new authority file /home/dcroxton/.serverauth.6879


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Avaux 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 20 19:07:10 2007
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) I810(0): Monitor 2 cannot be specified on single pipe devices
(II) Module already built-in
(II) Module already built-in
(II) Module already built-in
(EE) AIGLX: Screen 0 is not DRI capable
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

I've gone back to previous versions of xorg.conf, but none of them work anymore!  Help!

Sincerely,
Derek

---

### Post by dcroxton on 2007-10-21
I finally found a previous xorg.conf that worked.  I still have no idea what caused the crash, but I guess I won't worry about it now.

Sincerely,
Derek

---

