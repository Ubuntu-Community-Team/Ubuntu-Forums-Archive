---
title: "WUBI install error"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by Daemach on 2011-10-06
I was REALLY hoping wubi was going to work.  I've wanted to run Windows 7 and Ubuntu side by side for some time now.

Unfortunately, WUBI downloaded an amd-64 iso for the install.  I'm on an intel x64 machine.  That may have been ok but the install failed inside saying that it couldn't find a root filesystem.  I'm using fakeraid - maybe that's why.  In any case the install is now borked and it makes Ubuntu look ugly.

I would prefer to fix it if we can.  If not, how do I get back to booting straight into Windows?

---

### Post by Frogs Hair on 2011-10-06
See this thread , the problem has come up before . [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)  (WubiMega)

---

### Post by Daemach on 2011-10-07
> **Frogs Hair said:**
> See this thread , the problem has come up before . [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)  (WubiMega)

These instructions are for 10.x  I think WUBI installed 11.04.  I don't know enough about ubuntu to make changes like this without knowing if the version difference is going to cause problems.

---

### Post by Rubi1200 on 2011-10-07
Hi and welcome to the forums Daemach :)

The problem may well be because of the fakeraid. Officially, Wubi installs to RAID are not supported although we have seen some cases where it was possible.

I suggest you post the results of the boot info script so we can get a better idea of what is where on your system.

There is a link at the bottom of my post with instructions.

---

### Post by missmoondog on 2011-10-07
boot into Windows and go to control panel under programs, click uninstall programs. remove ubuntu and start over, is what i'd do.

this WILL NOT mess up your windows install.

---

### Post by bcbc on 2011-10-07
Raid 0 and 1+0 don't seem to work without some hacking. Easier to use a virtual machine.

To uninstall Wubi, go to Control Panel, Add/Remove programs, look for and double click on "Ubuntu".

Edit: yeah what missmoondog said. (I gotta use the preview button more).

---

