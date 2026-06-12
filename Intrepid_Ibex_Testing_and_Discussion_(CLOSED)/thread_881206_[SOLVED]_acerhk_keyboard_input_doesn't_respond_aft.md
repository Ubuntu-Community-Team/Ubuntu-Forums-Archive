---
title: "[SOLVED] acerhk keyboard input doesn't respond after recent updates"
date: 2008-08-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by klange on 2008-08-05
I have Acer laptop. I've been using the acerhk module for quite some time now to get my extra keys working. After the most recent set of updates, I get nothing. The module is loaded, and it itself works as I can trigger my LEDs with it, however, none of my media keys are responding.

Any ideas?

**e**: Turns out, with the update, everything is being reported a bit different, and most of my keys register with X86___ names rather than random keycodes. Reassigning everything in "Keyboard Shortcuts" fixed it.

---

### Post by ronacc on 2008-08-07
the august 5 updates messed with a lot of keymaps see bug#255008 .

---

