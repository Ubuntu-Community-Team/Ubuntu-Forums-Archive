---
title: "Plasma panel messed up"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lovinglinux on 2009-10-25
I don't know if it was an update, because I didn't reboot the machine for a while, but today my panels are messed up. Plasmoids order has changed and I can't change their positions anymore.

Anyone experiencing the same issue?

---

### Post by inportb on 2009-10-25
It may be because of the accumulation of development updates. I reboot my laptop quite regularly and haven't had much trouble with Plasma.

---

### Post by lovinglinux on 2009-10-25
> **inportb said:**
> It may be because of the accumulation of development updates. I reboot my laptop quite regularly and haven't had much trouble with Plasma.

I don't think so, because I have been updating frequently. It has something to do with my personal settings, since I have created a new user and it doesn't have the same issue. I'm trying to figure out which config files I should delete to reset plasma. If I delete all plasma related files under ~/.kde/share/config/ then I get a new panel with no plasmoids, but then a black screen shows up over the desktop. I can still launch applications via shortcuts tho.

---

### Post by Zorael on 2009-10-25
> **lovinglinux said:**
> I delete all plasma related files under ~/.kde/share/config/ then I get a new panel with no plasmoids, but then a black screen shows up over the desktop. I can still launch applications via shortcuts tho.
The files are those starting with plasma* in there, yes.

Black screen? As in, no background perhaps?

---

### Post by lovinglinux on 2009-10-25
> **Zorael said:**
> The files are those starting with plasma* in there, yes.

Black screen? As in, no background perhaps?

Black screen as in no desktop. No plasma, no wallpaper, nothing.

Anyway, I figured it out. It was compiz fault. Once I disable compiz and enable kwin the problem disappears and I can move the plasmoids again. I still need to figure out if it is a compiz issue or some compiz settings messing things up.

---

