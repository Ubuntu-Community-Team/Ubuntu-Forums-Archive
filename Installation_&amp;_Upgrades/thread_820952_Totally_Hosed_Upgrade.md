---
title: "Totally Hosed Upgrade"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by yerdon on 2008-06-06
Hi Ubuntu Experts,

I installed Edubuntu 7.04,upgraded to 7.10, then began the upgrade to 8.04.  The computer crashed in the MIDDLE of this upgrade and now it allows me to log in, but never shows me the desktop - just an off-yellow screen with a mouse pointer.

How can I restart the upgrade?  Or uninstall the part of the upgrade that I already did?

Am I completely dead in the water?  Pretty new at this...

HEEEEELLLLLLLLLPPPP!

Thank you!

Joseph

---

### Post by Sef on 2008-06-06
Since you get to the log in screen, see if you can do options and go into the terminal, then type in this code:

```
gksu "update-manager -c"
```

---

