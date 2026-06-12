---
title: "Chess/Go GUI's"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by Tikhon03 on 2010-04-03
I am having difficulty getting various Chess/Go GUI's to work.  My only success story so far is Gogui, which works brilliantly with indigo and mogo.  Here are the problems:

Qgo will install, but when staring a game against a go engine, the engine will not make a move on its turn.

gnome chess will install, but I am having problems setting up a game against the chess engines (similar to the problem with Qgo).

pychess will install but will not start: the program hangs right at the beginning.

No current download site for knights?!  The site
[http://knights.sourceforge.net/download.php?dist=source](http://knights.sourceforge.net/download.php?dist=source)
only takes me in loops!

I don't really need Qgo, since I have gogui, but it would be nice to get a chess gui working.  Any suggestions?

---

### Post by Lobais on 2011-03-08
Try PyChess again.
There were some problems between it and Ubuntu in the middle of 2010. They seam to be more or less gone now.

---

### Post by I2k4 on 2011-03-11
Using my LiveUSB Lubuntu 10.10, I was searching for a decent chess player today.  I gave up on DreamChess, which looked good, but wouldn't move unless dumbed down to easy modes.  I tested several.

(I know chess can be very challenging on minimal code, from an old Fritz 2D version for Windows that came on a 3" floppy and runs on practically no resources!  It's a killer.  Can't find anything up to it for Linux yet.)

So far, I'm getting good openings responsiveness out of GLChess.  It's noticeably slower in 3D than 2D, but I'm there for the game, not the graphics.  (Pychess, to my recollection, I rejected because the minimum interface was 1024X768, too big for my netbook, so I rejected without playing it.)

---

### Post by Tikhon03 on 2011-05-01
This problem has solved itself.  A newer version of Knights has been released that works with the current version of KDE.  Before this happened though, I tried compiling it from source.  It turns out that after getting to nearly the very end of the compiling process  I ran into an impassable roadblock: the older version of Knights relied on a sound server no longer used in KDE.  This made it impossible to compile, as Knights would not recognize the new sound server, and the version of KDE I had would not work with the old one.   In any case, for anyone interested, you can find the new version of Knights here:

[http://kde-apps.org/content/show.php/Knights?content=122046](http://kde-apps.org/content/show.php/Knights?content=122046)

---

