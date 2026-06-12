---
title: "Only get command prompt after upgrade"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2010-10-17
After upgrade to 10.10, I only get the command prompt.  Fortunately, all my XP Pro machines are running, and I am using one of them to access this Forum.

I suspect that nVidia graphics driver did not load correctly.  running startx at the command line gives numerous lines of text apparently understandable xorg gurus.  It looks like nvidia_drv.so did not load and module "nvidia" did not load [loader failed, 7] and next line says no drivers loaded.

In simple terms, how do I recover from this error?

John

---

### Post by cigtoxdoc on 2010-10-18
First, Ubuntu programmers should add some lines to error messages caused by X11/xorg to alert users that they should reboot, press ESC, and load Ubuntu in the failsafe mode.

Second, the problem in my case appears to be the failure of the nVidia drivers in 10.10 to work correctly with my graphics adapter. VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3) (prog-if 00 [VGA controller]).

Third, the workaround is to remove all the nVidia graphics drivers from the system and use the 1.9.0 driver provide The X.Org Foundation.

John:(

---

### Post by mikeashelby on 2010-10-21
I have this same problem... But fear I am more of a noob than you. Any chance you could talk me through the process of sorting this out?!

Feeling a bit annoyed, as this morning I had a perfectly good, working setup, and now I can't access anything! The same thing happened when I tried a different upgrade before, but I thought they'd haver fixed it by now... No such luck :(

---

### Post by petrafan007 on 2010-10-22
same here! and i have nvidia and installed the drivers separately as well i think what happened was i agreed to "remove/replaced" 83 files after the upgrade, and that fouled me up. help! lol

---

### Post by Psyb on 2010-10-25
I have the same problem I tried to upgrade form 10.04 to 10.10 and i have a nvidia geforce MX.

help please.

---

