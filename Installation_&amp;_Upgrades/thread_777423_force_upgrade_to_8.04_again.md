---
title: "force upgrade to 8.04 again?"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by fatagnus on 2008-05-01
Could I force the upgrade from 8.04 to run again even if i already upgraded before?
I had some dependency errors while upgrading (hit control-c when the focus was in the wrong window, the terminal in the upgrade dialog, this prevented a package to install) and I want to re-run it so those errors can be fixed.

---

### Post by bulldog on 2008-05-01
Try in a console:
 sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by fatagnus on 2008-05-02
Thank you,
I did, it seems that everything is ok and no package requires upgrades.

Now, I have some errors with emerald themes defaulting to the standard gnome window decoration, but that's another story.

---

