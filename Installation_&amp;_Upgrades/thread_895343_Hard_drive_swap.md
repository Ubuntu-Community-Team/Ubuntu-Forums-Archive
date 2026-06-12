---
title: "Hard drive swap"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by bravo sierra echo on 2008-08-20
Quick background: I've got a choice of two boxes, and I decided on the slightly faster one in the more attractive tower casing.  Unfortunately I've since discovered that the graphics card in it doesn't play nicely with Ubuntu, so I'm going to use the slightly slower desktop machine instead.

Can I simply swap the hard drives around?  The one in the tower is considerably larger, so I want to keep it.  What problems can I expect to see?  If they have different drivers, will Ubuntu recognise this and install the correct ones?  Or should I consider a full re-install?  Neither machine seems to have any "extra" drivers installed.

---

### Post by falcon61102 on 2008-08-20
You can switch the drives around, you just may have to tweak some of the drivers once you get the HD in place in the new machine.  Ubuntu is great for adaptability in that it will recognize and update most everything for you but you may have a couple things to do manually.  That's what makes it great for USB installs and whatnot... but yeah, you shouldn't have many problems with the switch especially if it's a simple hardware setup.

---

### Post by c2olen on 2008-08-20
I've done this plenty of times.
Usually, graphic cards differ, so some update in this scenario is required.
If you have no custom build kernel running, you should be fine. 

Of course, you really need to see if the architecture of your two boxes match. Are both x86_64 or i386. Or are both AMD? Otherwise you might need to update a great deal of packages to match your arch.

Gr.

---

### Post by Too Late on 2008-08-20
> **c2olen said:**
> Of course, you really need to see if the architecture of your two boxes match. Are both x86_64 or i386. Or are both AMD? Otherwise you might need to update a great deal of packages to match your arch.
Umm, I think you already know this, but there's only two  "basic" archs (on normal home computers). One is 32-bit (aka i386 or x86) and the another is 64-bit (aka x86_64 or AMD64 or something else).

---

