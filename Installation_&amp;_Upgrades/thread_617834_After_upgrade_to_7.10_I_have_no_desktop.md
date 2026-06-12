---
title: "After upgrade to 7.10 I have no desktop"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2007-11-19
After the upgrade the computer boots up normally to the desktop screen, but there are no contents.  All the files that should be on the desktop are still in the Desktop directory but they don't show up on the screen.  The other thing I noticed is if I pull down the Applications menu and ask it to install a launcher to the desktop that does work either.

I checked in /.config/user-dirs.dirs and the path to the desktop directory seems correct.

Does anyone have any ideas on how to fix this?

---

### Post by aysiu on 2007-11-19
Try this:

Press Alt-F2 and type ```
nautilus
```

---

### Post by Baasha on 2007-11-19
Bingo, that did it.  Thanks Aysiu.

On a related subject, how do I go about deleting a launcher from the Applications menu?  I have been searching through the Gnome documentation but haven't had any success.

---

### Post by aysiu on 2007-11-19
> **Baasha said:**
> Bingo, that did it.  Thanks Aysiu.

On a related subject, how do I go about deleting a launcher from the Applications menu?  I have been searching through the Gnome documentation but haven't had any success.
Right-click the Applications menu, and you should be able to edit it.

---

### Post by Achetar on 2007-11-19
Also, to have Nautilus start when you log in, you either have to turn on Desktop Saving, or put it in autostarted applications.

---

