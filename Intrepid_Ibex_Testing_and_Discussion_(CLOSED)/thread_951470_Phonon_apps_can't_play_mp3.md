---
title: "Phonon apps can't play mp3"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by membrive on 2008-10-18
Hi,

After the last upgrade, I can't play mp3 with phonon apps, like Amarok 2, JuK or DragonPlayer. By the other hand, I can play other media files like .m4a.

It's my problem or this is a bug? Any solution?

My system is Kubuntu Intrepid Ibex up to date.

**UPDATE: I haven't mp3 support in _any_ KDE app.**

---

### Post by membrive on 2008-10-18
Solved, I did:

```
$ mkdir ~/.xine/plugins/
$ cp -r /usr/lib/xine/plugins/1.24/ ~/.xine/plugins/
```

:guitar:

---

