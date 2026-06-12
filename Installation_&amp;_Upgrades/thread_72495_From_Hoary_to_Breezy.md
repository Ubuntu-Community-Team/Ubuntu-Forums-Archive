---
title: "From Hoary to Breezy?"
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by Midget on 2005-10-06
I was thinking about upgrading from hoary to breezy. I planned on changing the URLs in */etc/apt/sources.list*, but I wanted to check if there is anything else I need to do before/during/after the upgrade. I don't want things to break or anything :-P

---

### Post by Zelut on 2005-10-06
just follow the instructions at the end of the [www.ubuntuguide.org](www.ubuntuguide.org) for updating.  Simply update the sources (/etc/apt/sources.list), use apt-get dist-upgrade and you should be fine.

Note: I did the dist-upgrade first and everything worked fine with a few minor bugs.  A fresh install with the 5.10 CD worked the best.

---

### Post by Midget on 2005-10-07
[QUOTE=kuyaedz]just follow the instructions at the end of the [www.ubuntuguide.org](www.ubuntuguide.org) for updating.  Simply update the sources (/etc/apt/sources.list), use apt-get dist-upgrade and you should be fine.
[/QUOTE]

I have only found one bug so far - gdm complains about an unknown line in the config. Anyone else had this problem?

---

### Post by snowjunkie on 2005-10-07
I did a dist-upgrade last night.  It worked fine for the most part except for the following:

- During upgrade a lot of complaints about not finding locale (british.english), but everything seems fine.
- Link to evolution (still pointing at v2.2) had to be reset.
- It didn't remove Open Office 1.1 (removed it myself after - version 2 installed ok)
- Quake2 broke (still working on this)
- Xine Movie Player has gone missing?! (Totem is ok, but video/sound slightly out of sync).

If I find anything else wrong I'll update my post.  It was late, so I didn't get a chance to look around too much.

---

