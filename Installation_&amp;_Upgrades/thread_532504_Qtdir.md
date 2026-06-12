---
title: "Qtdir?"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by Dylnuge on 2007-08-22
I get this error when I compile LMMS from source:

```
checking QTDIR... configure: error: *** QTDIR must be defined, or --with-qtdir option given
```

Any help is appreciated,
Dylan

---

### Post by Tyl3r on 2007-08-22
Try
```
./configure --qtdir=/usr/share/qt3
```

---

### Post by Dylnuge on 2007-08-23
I tried ./configure --with-qtdir=/usr/share/qt3, but it gives the same error.

---

### Post by bfr on 2007-08-23
Do you have Qt3/KDE installed?  You, most likely, need it.

---

### Post by Dylnuge on 2007-08-23
Yes.

---

### Post by Dylnuge on 2007-08-25
Anyone.

---

### Post by Dylnuge on 2007-09-16
Okay, the $QTDIR variable is blank (at least, an echo gives me nothing).

Any help?

---

### Post by Dylnuge on 2007-09-18
I tried every combination I could think of, even tried it in KDE. Still, same problem.

---

### Post by fritsg on 2007-12-18
Install libqt3-mt-dev with Adept Manager or type sudo apt-get install libqt3-mt-dev and this error will go away

---

