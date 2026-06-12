---
title: "upgrade to Natty (11) - suddenly no desktop?"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by karlm on 2011-05-15
Last night I used my tower unit for the first time in weeks and it offered to upgrade to Natty.

I accepted the recommendation and left it to do it's job for an hour or so (it's an old machine with a slow processor)...


I then switched it off when it said it was safe to do so and took myself off to beddybyes.

This morning I booted it up again, salivating at the thought of a new & sexy desktop.... but lo' n' behold, there was no desktop!!!

I logged in as usual - there is just a background but no bars along the top, no icons to programs, no application/places/etc. menu - all gone.

The only way I could get online using the tower unit was to right click and select the 'get more themes online' which barked my firefox into life. I'm really not sure I want that to my uberace way of going online.

(If you're wondering, I'm connecting here via my windows laptop)

I'm not sure, as I didn't watch the install procedures, but it's as if it missed some of the upgrade out somewhere. The chance of a dropped packet or 50 is minimal as it is a hard-wired network connection to my router.

---

### Post by BlouBlou on 2011-05-15
Are you using NVidia GeForce FX 5***? It's a known bug, and waitting to be fixed.

While you wait to the patch, try using classic gnome, you can select it by GDM menu. So, in login screen, click on your user and in a box below select "Classic-session" or "Classic-ubuntu".

---

### Post by karlm on 2011-05-15
> **BlouBlou said:**
> Are you using NVidia GeForce FX 5***? It's a known bug, and waitting to be fixed.

While you wait to the patch, try using classic gnome, you can select it by GDM menu. So, in login screen, click on your user and in a box below select "Classic-session" or "Classic-ubuntu".

Cool!!! Thanks highly for this, I shall try it now!


ETA: This has worked... I assume a fix will come about soon?

---

### Post by BlouBlou on 2011-05-15
You need to unistall recommended drivers, reboot your system, install nouveau (experimental ones) reboot again and problem solved, you'll have 3D rendering working fine.

But you'll have this problem until Canonical/Community fix it: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/762478](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/762478)

---

