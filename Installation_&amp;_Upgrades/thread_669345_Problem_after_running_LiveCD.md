---
title: "Problem after running LiveCD"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by sporkubus on 2008-01-16
Hi, so I'm trying to install Ubuntu on a Pentium 4 with an onboard graphics card, but I run the LiveCD and when it should go to loading the desktop it just goes to a black screen with messed up colored lines on it. What am I doing wrong?

---

### Post by ARhere on 2008-01-16
Unfortunately it sounds like the Live CD has not been able to detect your graphics chip set properly.  This is a common problem with embedded video chip sets.

You could try using the Alt Install CD as it might have more driver options, but then you would be installing Ubuntu to a HDD.

Also, when the, "black screen with messed up colored lines on it." appears, try hitting CTRL+ALT+F2 and see if you get a command prompt.  If you do, then you could specify a different driver using the xorg.conf file.  There are a LOT of resources on editing this file on these forums but this is involved.

EDIT: Honestly a better solution would be to get a cheap graphics card of a name brand, like NVIDIA or ATI.  This will make life easier for ANY OS you are using.

-AR

---

