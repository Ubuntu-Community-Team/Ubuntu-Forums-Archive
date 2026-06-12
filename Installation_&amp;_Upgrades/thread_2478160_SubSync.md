---
title: "SubSync"
date: 2022-08-18
forum: Installation &amp; Upgrades
---

### Post by milpas on 2022-08-18
[COLOR=#000000]I just upgraded to 22.04.1. Everything works so far except SubSync, one of my subtitle editing programs.[/COLOR]

[COLOR=#000000]After upgrade it appears with the rest of the favorites icons but doesn't open when clicked. It also does not appear in my "Show Applications" list. I uninstalled SubSync via "Ubuntu Software"--which listed it as installed--, rebooted and reinstalled, again via "Ubuntu Software". But to no avail.[/COLOR]

[COLOR=#000000]Any other suggestions.[/COLOR]

---

### Post by tea for one on 2022-08-18
Is this a snap package?
```
snap list
```

---

### Post by milpas on 2022-08-18
Yes. it is in the snap folder. When trying to open the folders in the subsync folder, it just indicates it is loading, but nothing happens.

---

### Post by tea for one on 2022-08-18
Perhaps try to start it from the terminal and see if any error/warning messages appear.
I do not use subsync so I hope my guess is correct:-
```
/snap/bin/subsync
```

---

### Post by milpas on 2022-08-18
Tried. 
Result:
** (subsync:52333): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /run/user/1000/at-spi/bus: Permission denied08:51:37 PM: Debug: Failed to connect to session manager: Could not open network socket


(subsync:52333): Gtk-WARNING **: Error loading theme icon 'document-open' for stock: Icon 'document-open' not present in theme Adwaita
Segmentation fault (core dumped)

---

### Post by tea for one on 2022-08-19
Following a little research, this seems relevant:-
> Snap releases are temporary cancelled due to technical difficulties
Here is the source [https://github.com/sc0ty/subsync/releases](https://github.com/sc0ty/subsync/releases)

---

### Post by milpas on 2022-08-19
Thanks for the information.

---

