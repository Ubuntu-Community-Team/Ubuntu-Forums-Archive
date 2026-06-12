---
title: "Help! Can't get NTFS to resize...tried several different ways"
date: 2005-09-20
forum: Installation &amp; Upgrades
---

### Post by ChillyWilly85 on 2005-09-20
At first I tried using the Ubuntu 5.10 live cd to boot, and then use gparted to resize my NTFS partition...then I tried doing it through the actual install cd...neither way worked. Basically it would say that it was doing something, but on a restart nothing would have changed...

I need to resize my NTFS partition because i want to keep the data that's on it...but it's currently taking up my whole HD so I can't install Ubuntu until there's space for it...

Suggestions?

---

### Post by TristanMike on 2005-09-20
Does the same thing happen with 5.04 Hoary?

---

### Post by ChillyWilly85 on 2005-09-20
Dunno but i really don't want to spend another night downloading it...

---

### Post by matthew on 2005-09-20
Some ideas to try:

Turn off system restore in Windows and run system clean (or whatever it is called to clean out browser cache, temp files and all that) and then run defrag 3 or 4 times and try to get the ntfs stuff in as small a space as possible.

If you find some files that cannot be moved, see if you have something else running like ...um, stink, can't remember the name of it... Norton Utilities used to ship with a utility that ran in the background and did basically the same things as system restore but it started up before the os...man, what was that called??? Anyway, see if there is something like that installed, sorry I can't be more specific. If so, disable it. That should allow you to then resize the partition.

Hope one/all of these help.

---

