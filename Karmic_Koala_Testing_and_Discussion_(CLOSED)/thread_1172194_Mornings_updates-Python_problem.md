---
title: "Mornings updates-Python problem"
date: 2009-05-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-05-28
While updating this morning I get the following, which I am sure will sort out in the near future;
```
The following packages are BROKEN:
  python-brlapi 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 86.5kB of archives. After unpacking 115kB will be freed.
The following packages have unmet dependencies:
  python-brlapi: Depends: python (< 2.6) but 2.6.2-0ubuntu1 is installed.
The following actions will resolve these dependencies:

Remove the following packages:
gnome-accessibility
gnome-orca
python-brlapi

Leave the following dependencies unresolved:
ubuntu-desktop recommends gnome-orca
gnome-desktop-environment recommends gnome-accessibility
Score is -501

```
There were numerous Open Office updates as well that went okay.

---

### Post by plun on 2009-05-28
Its kept back for me..

```
The following packages have been kept back:
  python-brlapi

```

---

### Post by davideotape on 2009-05-28
I get this:

```
python-brlapi:
  Depends: python (<2.6) but 2.6.2-0ubuntu1 is to be installed
```

Is there a way to report missing dependency problems?

---

### Post by DougieFresh4U on 2009-05-28
I remember having 'orca' and 'python' drama back in the testing days of 'Jaunty'
I know I had a thread back then about it

---

### Post by taavikko on 2009-05-28
fix is released
```
brltty (4.0-6ubuntu2) karmic; urgency=low

 * Restore change from 4.0~svn4301-0ubuntu3, since otherwise brltty builds
   only with python2.5:
   - Bindings/Python/Makefile.in: Don't build with --quiet, call install
     with --install-layout=deb.
```

---

