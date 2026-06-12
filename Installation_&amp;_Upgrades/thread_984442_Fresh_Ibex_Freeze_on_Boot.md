---
title: "Fresh Ibex Freeze on Boot"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by halfB on 2008-11-16
Howdy
Fresh install of Ibex.  Boot goes through the full bar  with Ubuntu on top of it.  Then goes to brown screen with little white circle with moving dots.  Here is where it freezes completely after a couple seconds.   
I have removed compiz.  No change in freeze.
I have added noacpi in grub.  No change in freeze point.
What should I try next?

Thanks so much.
Eric

---

### Post by zenkoanlife on 2008-11-16
I'm having the same problem... when the login screen starts to load, the cursor freezes, followed by the bongo sound, then nothing, just a login box and frozen cursor.

---

### Post by spatterlight on 2008-11-18
Identical problem here. Ubuntu used to work.

---

### Post by edfromo on 2008-11-28
I had the exact same problem.  My solution was to press the key that looks like a cursor pointing at a page of text (the one above F9 on my Dell Inspiron 6400 keyboard).  I think this key is supposed to "select input method".

I have no idea why this solution should work, or why it locks up in the first place, but it seems to work reliably.  (I found it by pressing every key on the keyboard!)

PS - if that doesn't work, try 'num lock' followed by 'print screen'.  I think the problem lies with the X server.

---

