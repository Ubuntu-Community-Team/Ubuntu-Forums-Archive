---
title: "trying to dual boot 9.1  and winXP"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by bigdavejonnyt on 2009-12-16
Hi - trying to dual boot an XP machine with U 9.1. 

Insert disk

Reboot machine

Choose second choice install

screen flashes white u symbol on black for a very long time

finally pops a flashing command line prompt top left that you can't interact with


Confession time ; }

I went through this process once, got as far as the screen that allows you to choose to partition sizes, and had to shut down here to leave work. Never been able to get back to that screen.

Do I need to clear out some files ? Is there a flag set somewhere?

All help gratefully received!

Rgds

BDJT

---

### Post by darkod on 2009-12-16
Quitting the install process should not have made any changes to the computer. I'm talking if you click the Quit button in any of the 7 steps of course, not if you shut down when install is already under way.
Sometimes video driver issues can be a reason for this but if it allowed you to get to the steps once, can't see any reason not to work now.
How about selecting the Try Ubuntu option first? That will also show you if it will be running fine on your hardware.

---

### Post by bigdavejonnyt on 2009-12-17
Darkod, 

Thanks for getting back, and thanks for your suggestion.

So, I've tried a few things, including your suggestion.

I've tried the dual boot install as described

I've tried to load ubuntu from inside Windows, the installer says there was previous version of Ubuntu installed, and offers to remove it. The installer then gets part of the way through and bombs out. 

Are there log files produced in any of these processes I can look in for guidance?

I'll burn another iso, just to be on the safe side!

Thanks for your help, and...

Rgds

BDJT

---

### Post by darkod on 2009-12-17
If you are trying to install from within windows, that's different. It's called wubi, from Windows Ubuntu Installer. And it works in different way, the troubleshooting is also different.
Personally I don't use wubi, I prefer the proper dual boot on separate partitions. If you want to remove wubi you need to do it from add/remove programs like any other windows app.
When you tried the Try Ubuntu option what exactly happened?
And if you tried Install Ubuntu option again, it didn't work, as previously?

---

