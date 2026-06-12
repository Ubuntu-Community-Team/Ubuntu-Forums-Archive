---
title: "can't run package update"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by scharkalvin on 2007-08-09
After an update run hung and I rebooted the computer I tried to start it again.
I clicked on the orange '*' on the panel and entered my password.  I got a popup window with the message that the updater was already running (it was NOT, didn't see it in ps ax).  There must be a lock file stuck someplace that I have to delete (where?).
Or can I fix this by running apt-get from the command line?  With what parameters?
Thanks!

---

### Post by Pumalite on 2007-08-09
sudo pkg --configure -a
If that doesn't work, try: sudo dpkg --remove --force-remove-<packagename> (if you know the package that got stuck).

---

### Post by scharkalvin on 2007-08-14
I think you meant dpkg not pkg.

That, and sudo apt-get update    sudo apt-get dist-upgrade seem to be working

don't know if that will fix the lock on the graphical upgrade though.

---

### Post by Pumalite on 2007-08-14
Sorry for the typo.

---

