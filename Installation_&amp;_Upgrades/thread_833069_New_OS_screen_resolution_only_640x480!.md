---
title: "New OS screen resolution only 640x480!"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by iheartubuntu on 2008-06-18
We use a computer at work for playing our music. The HD crashed on it, so we decided to buy on of those Everex computers from Wal-mart for $199. Not a bad system (a bit slow with only 500mb memory) but its easily upgradeable to 2GB. And an 80GB HD is plenty for our needs. It had the old version of gOS installed, I didnt like it so I put Hardy Heron on.... looks great, works great except after reboot the screen resolution is stuck on 640x480. Ive got an older MAG 17" monitor hooked up to this computer, but i guess Ubuntu is not detecting it correctly? I dont care about the splash screen (which I see a lot of fixes for that rez), Im trying to fix my OS resolution! Any tips out there? I went into my menu.lst and added the vga=791 but it didnt do anything. What other options do I have? Thanks for any help. This is my first attempt to get my fellow coworkers to think a little outside the box and try a new OS.

---

### Post by Pumalite on 2008-06-18
Graphics card?

---

### Post by issih on 2008-06-18
Try going to the menu, right clicking and selecting edit menu's. In there somewhere is a "Screen's and Graphics" option, enable that.

Now launch that application and set your screen resolution in there.

Hope that helps

---

### Post by iheartubuntu on 2008-06-18
> **Pumalite said:**
> Graphics card?

The graphics card is whatever came with the Everex computer. The screen resolution was fine in the gOS... Im guessing 1024x768 and that would be fine if I can get it again.

---

### Post by iheartubuntu on 2008-06-18
Its stuck at 640x480 and 101 Hz.

---

### Post by avtolle on 2008-06-18
At the terminal (Applications>>Accessories>>Terminal)```
lspci
``` and post the output for review.

---

