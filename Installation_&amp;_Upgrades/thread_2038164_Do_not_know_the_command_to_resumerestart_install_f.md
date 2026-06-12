---
title: "Do not know the command to resume/restart install from a terminal"
date: 2012-08-06
forum: Installation &amp; Upgrades
---

### Post by LHammonds on 2012-08-06
I tried installing Lubuntu 12.04 onto an old IBM PC (using CD-ROM).

It froze up and I found out that it was because of a [bug in a webcam script]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/909179").

Well, after the install started, I pressed **CTRL+ALT+F1** to open a terminal prompt.  I issued the recommended command to delete the problematic file:

```
**sudo rm /usr/lib/ubiquity/plugins/ubi-webcam.py**
```Now I am sitting at a terminal window not knowing how to continue/restart the installation.

How can I go about finding out what command starts the install process?

EDIT: Solution is to press **CTRL+ALT+F7**

Thanks,
LHammonds

---

### Post by marinara on 2012-08-06
this is just a guess, but delete the file before ubiquity locks up.  ctrl+alt+f7 gets you back to ubiquity.  
you might use the alternate installer if you keep having problems

[https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall)

---

### Post by LHammonds on 2012-08-06
> **marinara said:**
> this is just a guess, but delete the file before ubiquity locks up.  ctrl+alt+f7 gets you back to ubiquity.  
you might use the alternate installer if you keep having problems

[https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall)
Thanks.  I'll see if that works.

The bug report says to delete it BEFORE starting the install, however, when booting from CDROM, you cannot access a terminal until you click "Install" from the boot menu.  Once you can see the first graphical "Continue" button, that is the point where you can press CTRL+ALT+F1 to access the terminal.  The lockup doesn't happen until several screens past the 1st one...it happens just before the user customization screen displays which is well before where I start the terminal to delete the cam script which should bypass it.

I'll give this a shot tonight and update the thread with the results.

Thanks,
LHammonds

---

### Post by efflandt on 2012-08-06
So try booting to a live system on install CD, delete the offending file, and then do the install from from the live system (there is install icon on desktop, and one in Unity bar if that works).

Note that the file will not actually be deleted from the CD, just from that live session.

---

### Post by LHammonds on 2012-08-07
efflandt, that is correct.  And yes, the remove command must be issued each time I try to install.

CTRL+ALT+F7 also got me back to the welcome screen. Thanks!

LHammonds

---

