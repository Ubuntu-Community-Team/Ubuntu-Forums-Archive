---
title: "ubuntu freezes so bad not even force quit works  :-("
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2010-06-09
hi all,

this is about my ubuntu 9.10 finally becoming unstable enough for even force quit to stop working.
well i use Ubuntu for everyday usage and have never had the OS freezing on me since the last 2 years or so. on the few occasions that there were problems, force quit was able to deal with the issue quite effectively.
however, this recent OS freeze happened when i was using firefox with transmission seeding in the background. ok, let me admit at the outset i had something like 6 - 8 tabs opened in 4 different firefox browser windows.
so all of a sudden the system just froze and it was so bad that i couldn't even use force quit as the entire panel had also frozen.
eventually i was able to log out using alt + F4 and restarting. however, although firefox started ok when i booted back in, the system restarted on its own within a few minutes and without any warning !

which leads me to the query - is there any other way in which one can use the otherwise effective force quit application ? i mean how to use it if the panel itself freezes ?

second, does this OS crash after more than 6 months of stable use indicate something about the general system health ? or is just one of those occasional problems one need not worry about ?

looking out for some useful tips on these topics !
thanks !

---

### Post by AM_SOS on 2010-06-09
hi all,
this is about my ubuntu 9.10 finally becoming unstable enough for even force quit to stop working.
well i use Ubuntu for everyday usage and have never had the OS freezing on me since the last 2 years or so. on the few occasions that there were problems, force quit was able to deal with the issue quite effectively.
however, this recent OS freeze happened when i was using firefox with transmission seeding in the background. ok, let me admit at the outset i had something like 6 - 8 tabs opened in 4 different firefox browser windows.
so all of a sudden the system just froze and it was so bad that i couldn't even use force quit as the entire panel had also frozen.
eventually i was able to log out using alt + F4 and restarting. however, although firefox started ok when i booted back in, the system restarted on its own within a few minutes and without any warning !

which leads me to the query - is there any other way in which one can use the otherwise effective force quit application ? i mean how to use it if the panel itself freezes ?

second, does this OS crash after more than 6 months of stable use indicate something about the general system health ? or is just one of those occasional problems one need not worry about ?

looking out for some useful tips on these topics !
thanks !

---

### Post by sanderd17 on 2010-06-09
duplicate of [http://ubuntuforums.org/showthread.php?t=1505785]("http://ubuntuforums.org/showthread.php?t=1505785")

---

### Post by dabl on 2010-06-09
Happily, true system "lockups" or "crashes" are pretty rare with Linux, but apparent lockups in which the screen goes black and/or the mouse and keyboard stop responding can happen - that is actually a crash of the X server only, or possibly some other process has run amok and is consuming 100% of the CPU resource.  If, immediately preceding the lockup you did NOT see a "kernel panic" message, then it is probably not a system crash, and you (and your filesystem) will have a brighter future if you will execute a graceful shutdown and reboot.  Here is what to do.

First, the mnemonic to remember:
[U]
R[/U]aising _S_kinny _E_lephants _I_s _U_tterly _B_oring

BEFORE you reach for that power switch, give the Alt-SysRq combo a chance to do a graceful shutdown/reboot.  Press and hold down "Alt-SysRq" ("SysRq" is the key otherwise known in DOS-world as "PrtScn", normally near the right end of the top row of keys) and then, one at a time, S-L-O-W-L-Y in sequence, " r s e i u b ".

Probably you will be amazed to see your "locked up" system do a shutdown and normal reboot.

Reference: [http://linuxgazette.net/issue81/vikas.html](http://linuxgazette.net/issue81/vikas.html)

---

### Post by cariboo on 2010-06-09
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by AM_SOS on 2010-06-10
yep, sorry !

---

### Post by AM_SOS on 2010-06-10
thanks a lot, dabl . pretty useful. will try this the next time i am in a fix !

---

