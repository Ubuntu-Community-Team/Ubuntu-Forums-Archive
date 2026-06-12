---
title: "(Metacity) Half of my Top Panel is gone!"
date: 2020-09-22
forum: Installation &amp; Upgrades
---

### Post by UbuntuWho on 2020-09-22
**HELP!!!** Several of my top panel icons and menus have disappeared, and I'm frantically trying to get them back!

I'm using Ubuntu 18.04.5, and my desktop environment is Metacity Gnome 3.30.1 (advanced from Gnome 3.28 using [this method]("https://askubuntu.com/a/1110988")). I recently updated my laptop, which included the latest kernel updates, and restarted. When I logged back in, an error popped up about some extension not running, and asked if I wanted to delete it. Without thinking, I clicked "Delete".

That, I think, is part of what makes the Metacity panel work! Now half of the icons and menus on the top tray are gone, including the menu with the logout/lock screen buttons, the time and date, and the system tray! All I have are app launchers that I manually moved to the top tray and the "Applications/Places" menus. I need to know what extension I just removed, and how I can get it back. I'm struggling to find them in Synaptic, but I don't even know what I'm looking for! I wish I had a copy of the error message, but I forgot to take a picture.

Does anyone know what I'm talking about here, or am I the only one with this problem? Any help at all would be vastly appreciated!

---

### Post by UbuntuWho on 2020-09-22
This is what my top panel looks like now:

[ATTACH=CONFIG]287004[/ATTACH]

My bottom panel is just fine, but most everything on the top is gone.

---

### Post by UbuntuWho on 2020-09-23
Got this via my Firefox web browser Gnome Shell extension: 
```
[COLOR=#ff0000]GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod:  No such interface &#8220;org.gnome.Shell.Extensions&#8221; on object at path  /org/gnome/Shell[/COLOR]
  **Check for GNOME Shell extensions update: **Your  native host connector does not support check for GNOME Shell extensions  updates. Probably python-requests package is missing.
```
I've installed *python-requests*, and am about to reboot. I'll see if this fixes it.

**EDIT: **Nope, did not. Also, I'm getting this error at *extensions.gnome.org/local/*:
```
Unable to locate GNOME Shell settings or version. Make sure it is installed and running.
```
Problem is, I already have Gnome Shell installed! Why doesn't it detect it?

---

### Post by UbuntuWho on 2020-09-23
I've since installed and switched to MATE, but I'd still like this issue fixed. If anyone knows what has happened, please tell me.

---

