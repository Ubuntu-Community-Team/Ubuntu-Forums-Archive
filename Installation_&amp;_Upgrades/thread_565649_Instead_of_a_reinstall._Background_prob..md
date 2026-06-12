---
title: "Instead of a reinstall. Background prob."
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by smurfit on 2007-10-02
Is there a way to default back to standard settings? Would be usefull.

Also, I can't alter my desktop background.  I get no errors when I configure my desktop - the picture just stays the same, but in the configuration it saves the changes.  Can I rectify this?  It only did this since I started playing with compiz.

---

### Post by peabody on 2007-10-02
Does it replace the background when you logout and back in again.

---

### Post by smurfit on 2007-10-02
Nope, never.

I have been looking all over for a fix, created more desktops & put different images on each one which by the way shows the same when you go back into the settings, but my actual image never changes. It just duplicates across other desktops.

What next?

---

### Post by peabody on 2007-10-02
Bad news is that it's likely a buried gconf setting.  One thing to try is to backup your ~/.gconf, ~/.gconfd, ~/.gnome* and ~/.nautilus folders and then logout, Ctrl+Alt+f1 to a VT, login and zap them with rm, then login again through the gui.  Should prove fruitful.

---

