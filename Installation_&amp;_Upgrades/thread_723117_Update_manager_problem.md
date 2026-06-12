---
title: "Update manager problem"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by Acunga on 2008-03-13
I get the following error while updating manager is on and i click to install updates manually from synaptic:
The following packages have unreasonable dependencies,Make sure that all required repositories are added and enabled in the preferences
Skype:
 Depends: dbus-x11 (>=1.0.0) but it is not installable
Obviously some Skye update has screwed up, but hwo to fix this, I have completely removed skype and now I get this while trying to install it again

---

### Post by taurus on 2008-03-13
Close down synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install skype
```

---

### Post by Acunga on 2008-03-13
The problem was that my other account was still working.As a newbie to Ubuntu I didn't knew that, when I switch between accounts, every program in the the previous account  remains fully functional.I mean I even have been hearing the sound from unconfigured skype and didn't realize it was from the 2nd account.
So the problem was skype was still working:mad::lolflag:
Anyway tanks for help and I hope I would of some help to future newbies of ubuntu.

---

