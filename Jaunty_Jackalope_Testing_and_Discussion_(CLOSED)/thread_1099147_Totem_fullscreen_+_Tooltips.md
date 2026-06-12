---
title: "Totem fullscreen + Tooltips"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by amauk on 2009-03-17
Bit of a strange bug,
not sure if I should open a bug report for it
as I have no idea what's causing it

Dual screen (nvidia twinview)
Totem video playing fullscreen on right screen

Any tooltips that pop up on the left screen cause the fullscreen movie to "flicker"
The background wallpaper briefly shows on top of the fullscreen video, then disappears

This happens with any tooltip when totem is in fullscreen mode
maximised totem (with window borders and nav bar) works as expected

Also, after totem flicker happens, any on-screen text box shows corrupted text,
text stays corrupted until text within is highlighted

I think this is a graphics driver issue,
but I have no way to tell....

Up to date Jaunty w/ Nvidia 180.37 proprietary driver
anyone else noticed this?

---

### Post by Nullack on 2009-03-18
Just another example of why Linux has a broken video architecture. The goodness will come with KMS, KMS drivers - proper gpu memory management.

---

### Post by captive on 2009-03-18
+1
This happens to me too.
(Jaunty 64bit nvidia 185)

Submitted bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/344759]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/344759")

---

### Post by mirko_3 on 2009-04-02
When's that?

---

### Post by edajai on 2009-04-02
KMS is one of the main features for the next Ubuntu release 9.10
Just need to hope that the nvidia and ati drivers adds stable support for KMS by then.

---

