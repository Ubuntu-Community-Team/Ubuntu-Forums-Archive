---
title: "Awn - can you run it with compiz ?"
date: 2009-11-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-11-21
I'm running Awn on Lucid and have some questions. Can you run Awn with compiz ? How would I switch windows as I assume that the bottom panel can be removed ? It sometimes appears in front of or behind the bottom panel. What about the wastebasket ?  I may be having some problems with Awn as it sometimes appears and other times I have to relaunch it via the Applications-Accessories menu and sometimes it disappears after opening new applications?
Comments please.

---

### Post by Toadinator on 2009-11-21
> **Kevbert said:**
> I'm running Awn on Lucid and have some questions. Can you run Awn with compiz ? How would I switch windows as I assume that the bottom panel can be removed ? It sometimes appears in front of or behind the bottom panel. What about the wastebasket ?  I may be having some problems with Awn as it sometimes appears and other times I have to relaunch it via the Applications-Accessories menu and sometimes it disappears after opening new applications?
Comments please.

Yes, you can. In fact it's preferred. AWN has a wastebasket/menu applet(s) and can also manage windows. Look at this thread for more information about the new version of AWN coming out and how to test it (I am and it's rock-solid stable): [http://ubuntuforums.org/showthread.php?t=1331413]("http://ubuntuforums.org/showthread.php?t=1331413")

---

### Post by ronacc on 2009-11-21
if you are running compiz enable the cube , then you can switch windows by rotating the cube . 
Edit : I meant desktops , minimised windows would appear in awn just like they do in the bottom bar .

---

### Post by Kevbert on 2009-11-22
Still having to relaunch awn every so often...maybe it's a bug.

Edit: Just launch awn from terminal and get a couple of problems:
```
$ awn
Screen is composited.
LOADED : /usr/share/applications/awn-manager.desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop
APPLET : /usr/share/avant-window-navigator/applets/awnsystemmonitor.desktop
APPLET : /usr/share/avant-window-navigator/applets/awnterm.desktop
APPLET : /usr/share/avant-window-navigator/applets/trash.desktop

(awn-applet-activation:3230): Vte-CRITICAL **: vte_terminal_set_background_image_file: assertion `VTE_IS_TERMINAL(terminal)' failed

(awn-applet-activation:3230): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.22.2/gobject/gsignal.c:2349: handler `51' of instance `0xa90000' is not blocked

```

---

