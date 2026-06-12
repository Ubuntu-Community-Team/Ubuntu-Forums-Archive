---
title: "Brightness Not Adjustable, NVIDIA Driver"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by caecusum on 2010-04-28
I'm running 10.04 on my new Thinkpad T510 along with the proprietary NVIDIA driver.  Brightness controls no longer work at all.  The buttons are recognized and the adjustment notification shows correctly, but the screen brightness does not change.

This worked fine initially when running the Nouveau driver.

Anyone come across a similar problem?

---

### Post by dv3500ea on 2010-04-28
This has been a problem for a long time but can be solved by installing a package called nvclock.

Then in System -> Preferences -> Keyboard Shortcuts
click add
set name to brightness-up
and command to: ```
nvclock -S +5
```
click add
set name to brightness-down
and command to: ```
nvclock -S -5
```

then set keyboard shortcuts for the commands.

---

### Post by caecusum on 2010-04-28
Thanks, this is my first NVIDIA-based laptop so I wasn't aware it was an existing problem.

I'll give your suggestion a try.

edit: nvclock does not work on my card.  A search on the web seems to indicate that it doesn't support newer cards and that this is a universal problem.  I'll keep looking.

---

### Post by 9AndS on 2010-04-29
Thanks! nvclock works for me.

---

