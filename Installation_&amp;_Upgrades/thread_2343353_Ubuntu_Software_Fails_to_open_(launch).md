---
title: "Ubuntu Software Fails to open (launch)"
date: 2016-11-15
forum: Installation &amp; Upgrades
---

### Post by aajax on 2016-11-15
When I try to launch Ubuntu Software it briefly displays an incomplete screen that resembles what is expected and immediately closes or fails.

Curiously, this behavior seems to be a direct result of allowing the Software Updater to update the system.  As it happens I am running multi-boot and have a second instance of the problematic system that seems to still function correctly.  Note:  the working system was created from an image of the problematic system and either is, or is close to, the same update status as the problematic system.  I've attached a screen shot from the properly running system of the Software Updater.  In that, this should be a pretty accurate portrayal of what was updated.  Needless to say I did NOT allow the upgrades and find myself in a precarious state until a resolution can be found.

Also, when the failure first occurred there were some dialogue box messages displayed, that I failed to capture, but the GNONE Software package was referenced as the cause of the error.

---

### Post by aajax on 2016-11-15
Going back to the failing system I was able to produce dialog box error and have now attached 2 more screen shots in order to show all of the details reported.

---

### Post by deadflowr on 2016-11-15
The crash report output shows that the gnome-software and gnome-software-common packages are obsolete.

If you close the software updater and then restart it, after it finishes reloading and shows the updates again, is there anything new listed for gnome-software?

Or perhaps try a more manual method from a terminal:
```
sudo apt update
sudo apt upgrade
```
choose n for no if you feel unsafe applying the updates.
you can copy/paste the output if you like.

---

### Post by aajax on 2016-11-15
The Software Updater seems to function normally.  When run it says the system is up to date.

Also this happened when I was trying to install a package.  I was able to install the package using Aptitude.

I think Aptitude is also showing that gnome-software & gnome-software-common are not using the latest version. As I said, this problem seemed to have been caused by allowing the Software Updater to apply updates.  I do recall that these gnome packages were on the list of packages to be updated.

Does the Software Updater maintain any kind of log that might provide more information?

---

