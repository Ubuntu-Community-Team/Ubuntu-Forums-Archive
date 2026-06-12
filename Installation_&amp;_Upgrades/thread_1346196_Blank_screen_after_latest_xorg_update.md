---
title: "Blank screen after latest xorg update"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by nadamsieee on 2009-12-04
The other night (either Wednesday or Thursday) I ran Update Manager, and I recall xorg being updated. The note mentioned something about default behavior if a xorg.conf was missing...

Now when I boot the PC, I get a blank screen. The monitor complains about "No Input Signal".

---

### Post by nadamsieee on 2009-12-13
I 'solved' this by renaming my xorg.conf file and letting the system generate a new one.

First I hit **CTRL ALT F1** to get to a new log-in shell (hit **CTRL ALT F7** to get back to your desktop).

Then I moved the 'offending' file (which prior to 'upgrade' worked):

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.20091204
```

Then I rebooted:

```
sudo reboot -h now
```

---

