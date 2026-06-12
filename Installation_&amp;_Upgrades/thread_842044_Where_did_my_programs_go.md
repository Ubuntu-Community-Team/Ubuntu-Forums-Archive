---
title: "Where did my programs go?"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by FargenDog on 2008-06-27
I installed some programs with the Package Manager and most of the programs I installed are not in the pull down menus.  I'm pretty sure they installed as there were no indications that they didn't load and some files are in various directories.  Where would I look for the executables?

---

### Post by iaculallad on 2008-06-27
Try to name some of the programs you installed that did not register on the Application menu.

---

### Post by sdennie on 2008-06-27
If you remember the names of the packages, you can usually find what executables they've installed with:

```

dpkg -L name_of_package | grep bin/

```

---

### Post by FargenDog on 2008-06-28
angband, Zangband, Valhala

couldn't find anything with grep.  Can I assume that the files would be in /bin or would that be where the install files would be?  (sorry newb here...)

---

### Post by oldos2er on 2008-06-28
Type "angband" in a terminal.

---

### Post by iaculallad on 2008-06-28
Try to find this application using the locate terminal command:

angband, Zangband, Valhala

```
locate angband

```
```
locate Zangband
``` or ```
locate zangband
```
```
locate Valhala
``` or ```
locate valhala
```

---

