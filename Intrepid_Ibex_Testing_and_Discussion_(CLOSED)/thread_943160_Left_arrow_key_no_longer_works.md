---
title: "Left arrow key no longer works"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jmillikin on 2008-10-09
Solved. Turns out Xorg in 8.10 returns different keycodes than in 8.04 for those keys, and it was running afoul of .Xmodmap.

------------

After upgrading to Intrepid, my left arrow key no longer moves the cursor. When I launch xev and press the key, it shows up as the ALT_L keysym. If I open GNOME keyboard settings, the layout looks like this:

[[img]http://ubuntuforums.org/attachment.php?attachmentid=87872&stc=1&thumb=1&d=1223608790[/img]](http://ubuntuforums.org/attachment.php?attachmentid=87872&d=1223608790)

If I change it to "United States / USA" layout, it looks correct and correctly detects the left arrow being pressed:

[[img]http://ubuntuforums.org/attachment.php?attachmentid=87873&stc=1&thumb=1&d=1223608790[/img]](http://ubuntuforums.org/attachment.php?attachmentid=87873&d=1223608790)

but all other windows still believe it's ALT_L being pressed.

I've changed the keyboard model to "Generic / Evdev-managed keyboard", as mentioned in the release notes, but this did not help.

---

