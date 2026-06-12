---
title: "Stuck with old logout dialog"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2008-10-09
How can I change the old session dialog:

[IMG]http://farm3.static.flickr.com/2162/2114471838_1601696a7a_o.png[/IMG]

to the new one? Seems some old hardy config prevents it from showing? :confused:

---

### Post by Hairy_Palms on 2008-10-09
open gconf-editor 
go to apps/panel/global/upstream_session and make sure its unticked

---

### Post by MacUntu on 2008-10-09
Already tried that (that's the way I enabled it in Hardy in the first place, except for setting the value to *true*). After the upgrade to Intrepid the key was gone, so I recreated it -  gconf-editor only says "This key has no schema" and the dialog stays the same.

---

### Post by MacUntu on 2008-10-10
*bump*

---

### Post by Hairy_Palms on 2008-10-10
what comes up if you run 
gnome-session-save --logout-dialog
and
gnome-session-save --shutdown-dialog

---

### Post by MacUntu on 2008-10-10
The new dialogs. *hmmmm*

---

### Post by Hairy_Palms on 2008-10-10
if you create a new user do they get the new dialogs or the upstream gnome ones?

---

### Post by MacUntu on 2008-10-10
New user gets the same old dialog.

---

### Post by Hairy_Palms on 2008-10-11
all i can think to recommend is to reinstall gnome-session and bash
sudo apt-get install --reinstall gnome-session bash

---

### Post by MacUntu on 2008-10-11
Thanks for your input but that didn't help as well (did a reinstall of gnome-session before and bash now).

I guess I just let this installation die and reinstall the RC because I've found two other bugs that I can't track down and that don't exist when using a Live-CD.

---

### Post by Hairy_Palms on 2008-10-12
ok, sorry i couldnt help more :(

---

### Post by psyke83 on 2008-10-12
The problem is that your panel is using the wrong applet. The older "Log Out..." applet is obsolete, and the functionality has been replaced in the "User Switcher" applet.

You can manually add it yourself, or simply wipe your panel configuration and avail of the new defaults.

---

### Post by MacUntu on 2008-10-12
Jup, finally fixed it. I had not only to remove --purge gnome-panel but also to delete everything "gnome-panel" related I could find with the search tool.

---

