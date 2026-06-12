---
title: "Gelemental crashes"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Miguel on 2009-10-03
Fellow ubunteros,

After getting help with compiling quantum-espresso in Karmic, I'd like to share with you another issue I've seen in karmic. There is a package of a periodic table, gelemental, that shows (showed) an element's properties if you click on it. It's similar to gperiodic or kalzium, for those KDE users. In Karmik, however, whenever I click on an element, gelemental crashes with the following message:

```

gelemental: symbol lookup error: gelemental: undefined symbol: _ZNK3Gtk6Widget9can_focusEv

```

I've already filled [bug #441453](https://bugs.launchpad.net/ubuntu/+source/gelemental/+bug/441453). Is there anybody else here experiencing this?

Thanks,

Miguel

---

### Post by Miguel on 2009-10-05
I just wanted to say that Cesare Tirabassi responded extremely quickly and the next Gelemental update fixed the issue. Yay!

---

