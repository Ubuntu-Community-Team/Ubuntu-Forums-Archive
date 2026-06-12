---
title: "Is there a way to change Nautilus' sorting method?"
date: 2010-01-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mdurham on 2010-01-11
Nautilus has started sorting upper-case and lower-case names separately. I find this quite annoying and wonder is there a setting somewhere to return it to the way of all previous Nautilus'?
Cheers, Mike

---

### Post by mdurham on 2010-01-11
Is it possible my problem has something to do with my weird locale?
Does anyone else have this or similar?

> mike@lucid32-6:$ locale
LANG=C
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=
mike@lucid32-6:$ 


---

### Post by BwackNinja on 2010-01-12
do a:

sudo locale-gen --purge

then logout and log back in.

---

### Post by mdurham on 2010-01-12
> **BwackNinja said:**
> do a:

sudo locale-gen --purge

then logout and log back in.

Thanks for that BwackNinja, but it didn't work. locale still produces the same list: LC_***="C"

Cheers, Mike

---

