---
title: "Alternate 10.4 64bit install hangs at 75%"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by Ojustaboo on 2010-07-02
Hi folks, I'm being driven nuts by this (not giving up though).

Had problems with hard drives yesterday, wouldn't recognise them after I'd installed Linux.  Today I fixed that problem (another thread on here) but now, every single time the install gets to 75%, it asks me to insert the CDROM and basically hangs.

Hitting enter doesn't try to fire up the CDROM, there's zero noise form it.

It did this once yesterday but all other tries worked fine.

Today it's failed the 7 different times I've tried, in exactly the same place, each time asking for the CD, even tried re-burning the CD, still failing at the same place.

It's just after doing something to APT, then storing something (not very helpful I know).

Can get a command prompt by CTRL-ALT_F2, but have no clue as to how to proceed when I get there.

Any and all suggestions welcome

Thanks

---

### Post by teisho on 2010-07-02
If you are posting from a different computer and have an internet router, I would suggest trying a netinstall.  That way you don't have to switch disks.  Just burn the Ubuntu 10.4 64 netinstall (only one disk instead of several).

If the problem persists, you can find out what command the installer was running when it stopped working by switching to a terminal.  Hit Alt+F2 to see virtual terminal two, and Alt+F1 to switch back to the install terminal.  You can see what's going on in the other virtual terminals by using Alt+ the appropriate F# key.

---

### Post by Ojustaboo on 2010-07-03
Thanks

Further investigation, the last thing it was trying to do was

> 
The following NEW packages will be installed
installation_report   libpci3  pcutils


The last two lines in dmesg are

> 
I/O error, dev sr0, sector 396
ISOFS: unable to read i-node block


I've burnt 3 different CD's so far, all from the same ISO, will download another iso from and see how I get in with that.

Failing that, will try a netinstall.

---

### Post by Ojustaboo on 2010-07-03
Gave up and did a netinstall, should have done this first, it worked 100% fine.

Thanks teisho

---

