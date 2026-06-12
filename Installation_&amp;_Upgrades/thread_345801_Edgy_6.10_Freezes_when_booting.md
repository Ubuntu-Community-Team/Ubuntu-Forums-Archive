---
title: "Edgy 6.10 Freezes when booting"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by siefer132 on 2007-01-24
Hey, I recently installed 6.10, and after a couple of times that i have booted into it, it started to freeze while booting. When it almost completes booting, it just freezes. If anyone could help me, it would be appreciated.[-o< 

Specs: Dell Inspiron 9400, Dual Core, 2gRAM, ATI Mobility Radeon X1400, 1.83GHz

p.s I'm also having resolution problems (in edgy), everything is sooo big, if anyone could help me with that too.

-Thanks

---

### Post by clpc on 2007-02-03
I have the same problem... but I think you will find that it is not actually frozen... if you leave it and wait then after about 10 mins it will suddenly pop up the login window and all is okay from then on.
I think this problem is something to do with Dual Core and nvidia drivers.
If you stick to the very slow and unusable vesa drivers then the login is fine but as soon as you install the nvidia drivers the problem exists.
if you do a dmesg in a terminal you will find entries like:
BUG: soft lockup on CPU#1 or CPU#0

I have no idea what the solution is for this other than waiting 10 minutes when you boot the PC.

Perhaps someone can help.

---

### Post by siefer132 on 2007-02-05
Yea, i got it fixed, i just re-installed, and now it works =D, but i didnt install the drivers yet.

---

