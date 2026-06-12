---
title: "After Breezy upgrade: memory allocation errors"
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by dentaku on 2005-11-21
After I finally got X/GNOME back up running (after upgrading to Breezy), many applications don't work anymore. If I run them from a shell, I see "memory allocation errors" ("Speicherzugriffsfehler"):

```

den@taku:~ $ oowriter2
/usr/lib/openoffice2/program/soffice: line 224: 11450 Speicherzugriffsfehler  "$sd_prog/$sd_binary" "$@"
den@taku:~ $ xine
Dies ist xine (X11 gui) - Ein freier Video-Player v0.99.3.
(c) 2000-2004 Das xine Team.
Speicherzugriffsfehler
den@taku:~ $ gxine
Speicherzugriffsfehler

```

---

