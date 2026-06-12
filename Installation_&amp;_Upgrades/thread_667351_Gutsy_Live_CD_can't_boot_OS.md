---
title: "Gutsy Live CD can't boot OS"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by BoltClock on 2008-01-14
**EDIT:** I managed to get into the OS only when I choose to start in safe graphics mode. My previous problem (the reason why I started this thread) is below the line.

Things are looking a bit loony, and at times the screen would flicker (especially when scrolling or dragging windows), but Ubuntu is functioning without any major problems. I can't get sound to work at all. Could there be hardware problems? I need assistance with this so I can determine whether my new PC welcomes Ubuntu (hopefully it will).

-----

I've read other similar threads whose posters have had problems with their Gutsy Live CDs. My problem doesn't seem to relate to any of those threads.

I'm on a new PC with the following specs that I know of and might be relevant:
- Intel Core 2 Duo 6750 2.66 GHz
- 4 GB RAM
- Palit N73PV motherboard
- Onboard NVIDIA GeForce7100 graphics card
- An unused 320 GB SATA hard disk on which I intend to install Ubuntu (the other disk, of 250 GB, contains a happily running Windows XP Pro SP2)

I downloaded the image, verified its checksum, burned it successfully and checked it with no errors found.

When I tried to start Ubuntu from the CD, it did a bit of stuff before stopping at a screen with the following messages:

```
 * Starting deferred execution scheduler atd  [OK]
 * Starting periodic command scheduler crond  [OK]
 * Checking battery state...                  [OK]
 * Running local boot scripts (/etc/rc.local) [OK]
```

Followed by that little blinking text cursor. Nothing seems to happen. Not even after waiting at least ten minutes. The only thing I could do was bail out of Ubuntu with Ctrl+Alt+Del.

Actually, **one** of the times I did manage to get past that part of starting the Live CD just led me to a warning that Ubuntu would be starting in low graphics mode instead because it couldn't find my graphics card (listed above). I don't recall what I did, but it just returned me to the set of messages above and stopped there again.

I don't dare to try altering any of the options (the string that shows with the F6 key), and I'm still very new to Linux so I need lots of help here. Thanks!

---

### Post by aysiu on 2008-01-14
That's weird. I don't know why it would just stop like that. Have you tried pressing Control-Alt-F7?

And, by the way, since it is a live CD, there is absolutely no harm to trying the options that show with the F6 key.

---

### Post by BoltClock on 2008-01-14
What does Ctrl+Alt+F7 do?

I don't know what options I can try. Will the help function tell me about those?

---

### Post by BoltClock on 2008-01-15
I'm on the live CD now. I haven't installed it yet.

Apparently it's caused by hardware incompatibilities because I managed to get into the OS only when I choose to start in safe graphics mode.

Things are looking a bit loony, and at times the screen would flicker (especially when scrolling or dragging windows), but Ubuntu is functioning without any major problems.

**EDIT:** I can't get sound to work.

Could there be hardware problems?

---

### Post by TUMS on 2008-01-15
Bump.
Same problem, using Ubuntu x64 DVD.

- Amd athlon 64 x2 4200+
- OCZ 2 Gb RAM (Dual Ch.)
- Asus M2N-E motherboard
- Asus EAH 2400 PRO graphic card
- 40 Gb WD hard drive.

---

### Post by BoltClock on 2008-01-16
Bump. I (or we) really, really need help here and no other threads provide a solution to my current problem. Perhaps I should change the thread title to reflect my new but possibly related issue.

---

### Post by TUMS on 2008-01-17
bump

---

