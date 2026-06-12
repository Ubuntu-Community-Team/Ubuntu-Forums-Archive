---
title: "Can't get rid of WINE?"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by tank.tmt on 2010-11-25
Hello,

I installed WINE via the software manager and then installed Civ 4. Then I tried to patch Civ 4 but it froze mid install so i restarted my comp. After it restarted I attempted to uninstall Civ 4 through WINE but it didn't work fully (i was left with a menu item under WINE in applications for it) I then attempted to uninstall WINE through the software manager, but WINE in the applications menu etc remained even though software manager says it is gone. I then tried to purge WINE which said it couldn't because WINE didn't exist - (sudo apt-get purge wine) and then I tried whatever this is (rm -R ~/*.wine*)

,both I got from other threads.
WINE still remains in the applications menu. I then deleted the folder from my home folder but the place in the menu still remains (the folder has gone).

How do I get rid of WINE and everything I brought with it completely? applications menu entry included as well as anything of civ 4 (i never tried to install anything else with it)

---

### Post by sanderd17 on 2010-11-25
you can go in synaptic package manager, search for "wine", right click and choose to "completely remove". This will also remove the settings. If this doesn't work, try to reinstall wine first

---

### Post by Goldfissh on 2010-11-25
> **sanderd17 said:**
> you can go in synaptic package manager, search for "wine", right click and choose to "completely remove". This will also remove the settings. If this doesn't work, try to reinstall wine first

This should work. I had a broken application installed which had to be re-installed first before I removed it. Annoying, but it works :D

---

### Post by jimmers on 2010-11-25
Try :-
  	 	 	 	p { margin-bottom: 0.21cm; }  sudo apt-get remove --purge wine1.2






Luck

---

### Post by sanderd17 on 2010-11-25
> **Goldfissh said:**
> This should work. I had a broken application installed which had to be re-installed first before I removed it. Annoying, but it works :D

When you do things and give no sign to the package manager (e.g. removing the .wine folder), the package manager first has to repair (reinstall) the program before it can totally remove it.

---

### Post by tank.tmt on 2010-11-25
Success with this

find $HOME -name '*wine*' -exec rm -r  '{}' \;

---

