---
title: "DESTROY created new reference to dead object ' Qt::SpacerItem'"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by f3tus on 2006-08-29
OK, this has been going for a while now... Everytime I do an apt-get upgrade and the files have been downloaded, ```
DESTROY created new reference to dead object ' Qt::SpacerItem', <> line 3 during global destruction.
``` echoes out in Konsole. Just before the packages get installed. What does that mean? Is there something wrong?

---

### Post by andrewc6l on 2006-11-11
It looks as if this is known and not harmful. See:
[http://mail.kde.org/pipermail/kde-perl/2003-December/000986.html]("http://mail.kde.org/pipermail/kde-perl/2003-December/000986.html")
for more details.

---

### Post by Bosonator on 2006-12-30
It's a problem that's typically encountered after one uses "automatix" or "easyubuntu". This thread describes how to fix it:

[http://www.ubuntuforums.org/showthread.php?t=208655](http://www.ubuntuforums.org/showthread.php?t=208655)

---

