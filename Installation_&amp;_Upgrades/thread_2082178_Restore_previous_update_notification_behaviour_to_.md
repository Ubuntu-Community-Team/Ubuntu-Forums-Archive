---
title: "Restore previous update notification behaviour to Oneiric"
date: 2012-11-08
forum: Installation &amp; Upgrades
---

### Post by Carl Foxmarten on 2012-11-08
I'd been using XUbuntu 11.04 for a while, but was recently forced into an upgrade to 11.10 Oneiric, and it changed the way the Update Manager told me about updates.

I ***HATE*** seeing the Update Manager popping up its own window to notify me that there's updates. The old notifier icon was far more polite.

Anybody know how to restore the old functionality?
The simple icon in the notification area?

---

### Post by Toz on 2012-11-08
I believe that you need to disable the notifier's auto-launch functionality. Open a terminal window and run this command:
```
gsettings set com.ubuntu.update-notifier auto-launch false
```

(You can reset this functionality by flipping the switch back to true):
```
gsettings set com.ubuntu.update-notifier auto-launch true
```

----------

To do this graphically, you need to install the package dconf-tools, run the dconf-editor, filter to com->ubuntu->update-notifier and make the change to the "auto-launch" key.

---

### Post by Carl Foxmarten on 2012-11-12
Ah! That did it!

Since when did they switch from gconf to dconf?
And why is gconf still installed?

Just like a Gnome tool, though... >.<

---

### Post by Toz on 2012-11-12
As far as I know, the transition from gconf to dconf is ongoing. Perhaps this link might help: [http://askubuntu.com/questions/122039/dconf-editor-and-gconf-editor]("http://askubuntu.com/questions/122039/dconf-editor-and-gconf-editor")

That link links to 3 other documents that attempt to explain the differences.

---

