---
title: "Gedit uninstalled, causing other issues"
date: 2009-12-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-12-03
I accidently uninstalled gedit.  When this occured I got gedit:
 Depends: python-gtksourceview2 but it is not going to be installed while trying to reinstall it.  This also uninstalled ubuntu-desktop.  Is there a way to reinstall Gedit without totally borking my machine? 

python-gtksourceview2 gives me: python-gtksourceview2:
 Depends: python2.5-gtk2  but it is not installable

---

### Post by DougieFresh4U on 2009-12-03
> **sox fan Matt said:**
> I accidently uninstalled gedit.  When this occured I got gedit:
 Depends: python-gtksourceview2 but it is not going to be installed while trying to reinstall it.  This also uninstalled ubuntu-desktop.  Is there a way to reinstall Gedit without totally borking my machine? 


I did the same _**exact**_ thing a few days ago. I didn't reboot until after updates later in the day that fixed all up real nice nice.

---

### Post by sports fan Matt on 2009-12-03
Ok, i'll just wait.  Mine I assume was caused by i think trying to uninstall things like certain python apps and tomboy and ttf extras i didnt want.

---

### Post by alphacrucis2 on 2009-12-03
> **sox fan Matt said:**
> Ok, i'll just wait.  Mine I assume was caused by i think trying to uninstall things like certain python apps and tomboy and ttf extras i didnt want.

I don't think that is the reason. Anyone doing an update followed by a dist-upgrade will find it wants to remove gedit and python-gtksourceview2 at the moment. It's because of package dependencies in the repos. Best to do a safe-upgrade.

---

### Post by sports fan Matt on 2009-12-03
I have now lost (as in not showing up: adminstration menu: everything except software center, and no preferences menu.  What was in the preferences menu, anyone have a list?  And I have 2 firefox menu entries.  One for Shiretoko and one for Firefox 3.5.  :confused: What the heck happened?

---

### Post by nperry on 2009-12-03
> **sox fan Matt said:**
> I have now lost (as in not showing up: adminstration menu: everything except software center, and no preferences menu.  What was in the preferences menu, anyone have a list?  And I have 2 firefox menu entries.  One for Shiretoko and one for Firefox 3.5.  :confused: What the heck happened?

[http://ubuntuforums.org/showthread.php?t=1344744](http://ubuntuforums.org/showthread.php?t=1344744)

Bug has been raised, assigned and in progress!

---

### Post by sports fan Matt on 2009-12-03
Phew!  I hadnt had a ton of time to check these things out today :)

---

### Post by sports fan Matt on 2009-12-03
So to upgrade now: sudo aptitude safe-upgrade?

---

### Post by nystire on 2009-12-05
It appears to be fixed now. Try to reinstall it (and ubuntu-desktop while you are at it :) ).

---

### Post by sports fan Matt on 2009-12-05
After having issues with my computer I think Im finally back but time will tell.  All the updates plus a reinstall of ubuntu desktop have seemed to work.

---

