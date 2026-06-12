---
title: "Samba installation problems"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by kdvgent on 2007-11-04
I installed samba on my fresh Kubuntu.  I installed it via Add/Remove Programs.

This generated two new entries in my menu tree, both named Samba (one under "Sttings" and one under "System").  Clicking on these entries does not lead to any action.

Checking things, they both generate the command "gksu system-config-samba".  Entering that command via a terminal made it clear that the gksu application was not automatically installed as part of the samba installation (problem or bug?).  Hence I installed it myself via Adept.

Clicking on the menu items still does not lead to anything.  Entering the command via a terminal gives now the error-message: "system-config-samba requires a currently running X server".  But of course, I have an X-server running - how should I otherwhise use KDE.  (problem or bug?)

Help please.  I have used gentoo before and hence I have no problem starting hacking configuration files but I would hope that there would be an easier method.

Regards and many thanks in advance for your help.

---

### Post by kdvgent on 2007-11-06
Searching on the web gave me some clues.

The problem is a dependency problem that is not picked up by adept.  I had to install two additional packages (and their dependencies): python-gtk2 and python-glade2 to make things work.

---

### Post by imolafem on 2008-06-30
Thank you so much for figuring this out and posting the answer!

---

