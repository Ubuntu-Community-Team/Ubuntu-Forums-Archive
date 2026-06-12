---
title: "Usplash: how hard can it be?"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by gwi on 2006-12-09
I installed Edgy on three computers:
1. Celeron 800MHz, Intel 845 integrated graphics adapter, EIZO CRT
   Did a fresh install on this one. On startup and shutdown it shows (in textmode) a more or less random pattern of white and black blocks. Screen is flashing.

2. Pentium 4, 3GHz, Intel 965 integrated graphics adapter, same Eizo CRT as above
   Did an updgrade (using update-manager -c). On startup and shutdown shows either a black screen with a flashing cursor in the upper left corner (with option "quiet", or messages showing what's going on (without "quiet").

3. AMD64, 2GHz, nVidia PCS5300 graphics adapter, Eizo LCD
   Did an updgrade (using update-manager -c). On startup and shutdown shows a video test screen.

So, three different systems all running Edgy, three different splash things happening. What is so difficult about it? I know Edgy is said to be less stable than Dapper, but this splash thing doesn't even deserve the "beta" label.

I tried several "solutions" that are mentioned in these forums, but nothing that can make either of the three systems above show the Edgy usplash.
Both upgraded systems did show the Dapper usplash normally.

Nice to see instructions on customizing the usplash, but before I do that, I want to see the original Edgy usplash (just to make sure it is working).

So my question: can someone tell me what's wrong with usplash, and how can it be fixed?

---

### Post by Jivicin on 2006-12-11
I'm having the exact same problem you're having in #2.  I have yet to find a working solution.

Any help would be much appreciated!

---

### Post by mcduck on 2006-12-11
you could try adding 'vga=792' to the end of the kernel line to make Ubuntu boot at 1024x768.. There are also other resolution/color depth possibilities but I can't just now remember where to find a table..

And make sure you still have the 'splash' in the kernel line too ;)

---

