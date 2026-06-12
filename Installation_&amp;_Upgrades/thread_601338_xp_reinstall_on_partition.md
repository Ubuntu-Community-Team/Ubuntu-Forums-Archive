---
title: "xp reinstall on partition"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by thepopasmurf on 2007-11-03
I have a dual-booted laptop with Gutsy Gibbon and xp.
However, my XP partition keeps on getting a blue-screen when I try to startup so I'm thinking of reinstalling it.

So I was wondering, if I try to reinstall xp will it get rid of my ubuntu partition?

---

### Post by dantrevino on 2007-11-03
Microsoft assumes you don't want any alternative and its boot loader will blow away grub.  You don't deserve a choice in Microsoft's eyes.

Sounds to me like instead of re-installing xp, you should reclaim that disk space for Ubuntu :).

dan

---

### Post by thepopasmurf on 2007-11-03
unfortunately I share the computer and still needs to be used

---

### Post by PmDematagoda on 2007-11-03
If you reinstall XP, then very usually Grub will be overwritten by the Windows MBR. If you do face a problem like that after installation. Use SuperGrub found here:-

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

I would advice you to get and burn the SuperGrub disc or make the SuperGrub USB before re-installing XP.

---

