---
title: "New Login Window"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by The Recorder on 2009-10-01
Karmic new login working fine (although I find it a little frustrating that I can't see what's going on when a disk check is taking place during boot).  However, there is a little cosmetic thing that is driving me crazy.  In the login window, in the login box (where I choose my name), there is a logo at the top of the box.  In my case, the logo is a "X"ubuntu one.  I have a number of desktop environments and window managers installed (including xubuntu, ubuntu, and kubuntu), and I have no idea why it chose the xubuntu logo to place there, but I would like to change it to something else; perhaps an ubuntu logo.  I have searched these and other forums, the Web, and numerous files on my computer for hours, but I can't find anything on this matter.

Does anyone have an idea of how this change could be made?

---

### Post by Mike_IronFist on 2009-10-02
Typically the last desktop environment you install leaves its mark on your default settings by changing them to its own. The way I usually remedy this is by removing said package, or reinstalling the default package.

I don't know what the login screen packages are this time around, but the rule should be fundamentally the same: if you uninstall the package for Xubuntu's login screen and reinstall the Ubuntu one (be it still installed or not) it will probably restore your login screen to normal.

---

### Post by The Recorder on 2009-10-02
> **Mike_IronFist said:**
> Typically the last desktop environment you install leaves its mark on your default settings by changing them to its own. The way I usually remedy this is by removing said package, or reinstalling the default package.

I don't know what the login screen packages are this time around, but the rule should be fundamentally the same: if you uninstall the package for Xubuntu's login screen and reinstall the Ubuntu one (be it still installed or not) it will probably restore your login screen to normal.

THANKS MUCH!!!

"Completely" uninstalled "xubuntu-gdm-theme" package, and then reinstalled the "ubuntu-gdm-themes" package, and the entire login screen (box, icon (now a "human" computer), fonts, colors, "other" icons, etc.) displayed as intended .

Again, thanks a million.

---

