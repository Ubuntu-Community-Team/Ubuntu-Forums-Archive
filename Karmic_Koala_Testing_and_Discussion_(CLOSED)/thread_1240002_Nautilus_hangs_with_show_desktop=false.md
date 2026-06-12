---
title: "Nautilus hangs with show_desktop=false"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-08-14
I got me a bug in Nautilus. Change the gconf setting /apps/nautilus/preferences/show_desktop to false, and nautilus hangs. All I get is a busy cursor on the desktop, and I can't open any file manager windows with nautilus. CPU usage goes up, but nothing shows in top. Change the setting back to true, and all is well.

Could some one confirm please?

---

### Post by phenest on 2009-08-14
More observations of this bug:

The window list on the gnome panel will fill up with buttons showing Nautilus as 'starting'. Setting show_desktop=true again, and all those buttons disappear.

After setting showdesktop back to true, all my volumes have been mounted.

EDIT: I just tested this with alpha 4 Live CD.

---

### Post by dinxter on 2009-08-14
> **phenest said:**
> I got me a bug in Nautilus. Change the gconf setting /apps/nautilus/preferences/show_desktop to false, and nautilus hangs. All I get is a busy cursor on the desktop, and I can't open any file manager windows with nautilus. CPU usage goes up, but nothing shows in top. Change the setting back to true, and all is well.

Could some one confirm please?

it sure does, do you have a bug filed yet? i'll confirm

---

### Post by phenest on 2009-08-14
I'll do it now.

EDIT: All done: [bug 413568]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/413568")

---

### Post by dinxter on 2009-08-14
whoops, i missed this [https://bugs.launchpad.net/nautilus/+bug/325973](https://bugs.launchpad.net/nautilus/+bug/325973) so [bug 413568]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/413568") is a duplicate of that

---

