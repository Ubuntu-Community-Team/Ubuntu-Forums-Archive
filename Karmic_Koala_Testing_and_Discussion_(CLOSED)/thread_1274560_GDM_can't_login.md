---
title: "GDM can't login"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nimbrant on 2009-09-24
After recently upgrading to karmic from jaunty I can no longer login to gnome.

After logging in at login screen i get the default gnome login sound (sometimes it does not complete) then I get kicked back to gdm.

no errors in xorg log.

i can boot into recovery mode and do startx, which loads gnome as root, but for some reason i cannot log in as a regular user.


i tried to do apt-get update and apt-get upgrade, but that did not work for me.

im not sure what to do next or how to debug this issue.

---

### Post by PauGNU on 2009-09-26
Same problem here. But I cannot log in even through the terminal or root.

---

### Post by moviemaniac on 2009-09-26
try ctrl+alt+F7 when you hit the command prompt.

It's a known bug: [https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/430494](https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/430494)

---

### Post by llamakc on 2009-09-26
Same issue here. I had to roll back to a previous kernel to get in.

---

