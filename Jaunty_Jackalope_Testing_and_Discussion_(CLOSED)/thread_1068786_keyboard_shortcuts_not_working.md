---
title: "keyboard shortcuts not working"
date: 2009-02-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by alongenemylines on 2009-02-13
Anyone else having this issue?  It started a few days ago, at the same time that compiz broke.  Compiz got update and fixed, but still no keyboard shortcuts work.  Strangley though, the web/mail/calc hotkeys on my logitech internet 350 work, but alt + F2, alt + F1, etc etc don't.

---

### Post by scaine on 2009-02-13
No ALT-F2 here either.  I've stuck a run icon on my panel for the time being.  I'll log a bug over the weekend if updates don't fix it.

---

### Post by OliW on 2009-02-13
Load up ccsm (install compizconfig-settings-manager if you don't have it) and check the Gnome Compatability plug-in. This should restore your Alt+F1 and Alt+F2...

.. Assuming you're using compiz. If you're not, then... No idea =(

---

### Post by scaine on 2009-02-14
Great shout OliW - that setting in Compiz fixed my keyboard shortcuts.

Do you know the history of that plug-in?  Is it enabled by default in Intrepid, but not in Jaunty?  I'd never heard of it until you posted...

---

### Post by OliW on 2009-02-14
As far as I know, it's new so It didn't exist in Intrepid...

It's definitely something that should be enabled by default. I ran into the same problem when I upgraded from Intrepid... 

I'm not sure if it's enabled on new installs, but somebody should make surethis gets fixed for upgraders.

---

### Post by scaine on 2009-02-14
I've created a bug for this :
[https://bugs.launchpad.net/ubuntu/+bug/329395](https://bugs.launchpad.net/ubuntu/+bug/329395)

Please add "affects me too", even if you've already manually added the workaround!

I should probably have added that my Jaunty install is a fresh install from about two weeks ago, not an upgrade.

---

### Post by philinux on 2009-02-14
I've unchecked and check this Gnome Compatability plug-in. Still no shortcuts work.

AHH. Keyboard shortcuts are working. The ones I tested were customised, they dont work but the old ones do even though in the gui they are different.

[edit] blow me if the two I was testing are the two under gnome compatibility. Changed them under this option and they now work with compiz on.

---

