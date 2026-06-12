---
title: "make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by Death_Sargent on 2007-03-15
I have been trying to install Flash For Linux via the make command.

./config does not work so i figured use make then check install but all i get is this

```
make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'. Stop.
```

I check the file and all gedit shows me is a blank file 

I used (sudo gedit `/usr/share/qt3/mkspecs/default/qmake.conf')

What should i do to get this to work

---

### Post by cyberface on 2007-11-15
Installing qt3-dev-tools should do the trick.

Regards

---

