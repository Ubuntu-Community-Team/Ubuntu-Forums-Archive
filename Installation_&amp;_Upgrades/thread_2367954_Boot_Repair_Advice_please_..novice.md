---
title: "Boot Repair Advice please ..novice"
date: 2017-08-05
forum: Installation &amp; Upgrades
---

### Post by boogiedil on 2017-08-05
[http://paste.ubuntu.com/25241919](http://paste.ubuntu.com/25241919)
Thanks in advance

---

### Post by boogiedil on 2017-08-05
Link in previous post was from a run of Boot Repair executed from within a CD/Trial session. (seemed the easiest thing to do since I had an installer loaded)
I subsequently created a boot disk with Boot rrepair on it. Ran Boot repair from bootable Cd. Seemes to be doing different things than the one from within a trial/Cd session.
I'll see what results are.

---

### Post by boogiedil on 2017-08-05
Boot Repair 64bit run from a boot disk did heaps more. At one point it asked which partitions? to create grub on. It said install on all if in doubt. So I checked all. However the command line progress display said it could be unreliable. So not sure if I should re-do the whole boot repair thing.
However the laptop DOES NOW BOOT into Ubuntu 16.4 albeit somewhat slow.
All credit to the Boot Repair team !! Amazing.
Happy to hear any comments otherwise I'll assume this thread closed.
Should have created Boot Repair boot disk in the first place I guess.

---

### Post by vasa1 on 2017-08-05
> **boogiedil said:**
> ...
Happy to hear any comments otherwise I'll assume this thread closed.
Should have created Boot Repair boot disk in the first place I guess.
You could mark this thread [SOLVED]: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by johndough2 on 2017-08-05
Hi

COMMENT:  

It is a 120 gig disk, you are using 115.6Gb ish as root and an extended as a swap file of 1.6Gb?

Personally I would want a \ root of about 37 Gb and then a \ home of  77Gb leaving the last part as Swap.
I would not make an extended in the above case, and would hope the different layout and slightly bigger swap would improve the throughput.

---

### Post by boogiedil on 2017-08-05
Points taken. Thanks for patience.

---

