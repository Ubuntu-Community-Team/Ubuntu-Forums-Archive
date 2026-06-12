---
title: "Installation problem"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by RageWarp on 2007-10-22
Alright, here we go again. I took a little hiatus from screwing around with ubuntu becuase I just wasnt able to install it for the life of me. Ive tried every different type of install over the last few versions of ubuntu(not including the alternate which was a different prob).

I get to the point where its going through a sort of check list with [OK]'s on the right hand side(it takes a considerable amount of time to get to this stage)and when the list has completed i am left with a blank screen to stare at, no blinking cursor.
Im going to make an educated guess and say its a hardware conflict of some sort, so here are my specs.

Asus m2n-sli deluxe mobo
amd am2 3800+ x2 cpu @2.0ghz
1gb of corsair ram
Nvidia 7600gs x2

---

### Post by RageWarp on 2007-10-23
anything?

---

### Post by RageWarp on 2007-10-24
no?

---

### Post by RageWarp on 2007-10-25
bump

---

### Post by dabang on 2007-10-25
I have similar hardware but never had a problem booting Ubuntu. Though, booting a Kubuntu 7.10 CD gave me a blank screen at the end. What helped in my case was

- starting X new by pressing Crtl + Alt + Backspace

or (which is nicer)

- switching to tty8 (or 7?) by pressing Alt + F8. (Or maybe F7, not sure anymore).

If this doesn't help, press "F6" at the boot screen and add "noapic" as kernel option. You my also try "acpi=off" if the former doesn't work.

Don't know if this helps, but it'll be be my 2 cents...

---

### Post by RageWarp on 2007-10-25
I have tried the noapic command on multiple occasions but still end up the same. Ill try the other options you have presented

---

### Post by RageWarp on 2007-11-03
bump

---

