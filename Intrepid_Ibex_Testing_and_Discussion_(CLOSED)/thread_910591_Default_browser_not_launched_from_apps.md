---
title: "Default browser not launched from apps"
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DavidONE on 2008-09-04
My default browser is Firefox (defined in 'Preferred Applications').  In a few places (e.g. FontMatrix->About, Gnome Do->Google Search plugin) links open in Opera.

Any suggestions, please?

---

### Post by OliW on 2008-09-04
sudo update-alternatives --config x-www-browser

---

### Post by DavidONE on 2008-09-04
Thanks.  That fixed it.

Is this worthy of a bug report?  I'm assuming that 'Preferred Applications' should have taken care of this?

---

### Post by jfernyhough on 2008-09-04
Hmm... I had this problem after installing Opera, but then running Preferred Apps again and pointing it to Firefox (a /home/j/bin copy of 3.1pre) sorted it again.

I'd say this is worth a bug report as your settings are being overridden (or just changed) when a new browser is installed.

---

### Post by DavidONE on 2008-09-10
After a bit of searching it looks like this is an old bug that has been given low priority:
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/150891](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/150891)
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/252186](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/252186)
+ lots more reports

This, for me, is one of those little things that should be *high* priority.  It gives the user an impression of low quality because it seems like random behaviour.  Much the same as [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/252902](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/252902)

/rant :)

---

