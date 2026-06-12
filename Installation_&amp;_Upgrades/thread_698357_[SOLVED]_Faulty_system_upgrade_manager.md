---
title: "[SOLVED] Faulty system upgrade manager?"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by couzin2000 on 2008-02-16
```
xserver-xorg-video-intel
X.org X server -- Intel i8xx, i9xx display driver
From version 2:2.1.1-0ubuntu9 to 2:2.2.1-0ubuntu9.1 (Size: 173KB)
```

I'm getting this in my System upgrade window. Thing is, *I do not use Intel graphics card* in my desktop, it's a **Nvidia Gigabyte GeForce 7300 GT**. I don't think I should download/install this upgrade, because I've had so many troubles trying to simply configure the system to work with an Nvidia TV-out, at this point I don't wanna touch it.

However, I would love to know how to make sure this upgrade notification go away. I'm pretty sure I shouldn't be getting this message.

---

### Post by Jussi Kukkonen on 2008-02-16
You have that package installed already, so you naturally also get new versions. This doesn't mean the driver is actually used. Ubuntu installs all drivers I think (as dependencies to xserver-xorg-video-all) probably so we wouldn't end up in problems when we change graphic cards...

AFAICT you can safely remove xserver-xorg-video-intel if you want to, but upgrading the package really shouldn't break anything either.
.

---

### Post by couzin2000 on 2008-02-16
Thanks Jussi,
just upgraded the file and everything still runs smooth as a baby's butt. Gracias amigo!

---

