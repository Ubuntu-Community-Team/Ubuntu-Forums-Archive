---
title: "installation problems"
date: 2005-08-18
forum: Installation &amp; Upgrades
---

### Post by suxxors on 2005-08-18
i am newbie...and my english is bad but i try to explain

i have trouble with installing ubuntu. I have original cd ( this free shipping stuff ). If i am installing ubuntu, it is doing restarts and i have to begin from beginning. It is doing restart  everywhere not on specific place. Sometimes there where i choose language, sometimes hardware detecting place. same problems with live cd.

my cpu:
Pentium III, Hp brio BA600, 550mhz, 
graphic: maxtor g200,

---

### Post by askreet on 2005-10-29
It sounds like you have a hardware problem with that computer, if I had to guess.
Run some diagnostics on the hardware, see how they come out.

---

### Post by codejunkie on 2005-10-29
[quote=suxxors]i am newbie...and my english is bad but i try to explain

i have trouble with installing ubuntu. I have original cd ( this free shipping stuff ). If i am installing ubuntu, it is doing restarts and i have to begin from beginning. It is doing restart everywhere not on specific place. Sometimes there where i choose language, sometimes hardware detecting place. same problems with live cd.

my cpu:
Pentium III, Hp brio BA600, 550mhz, 
graphic: maxtor g200,[/quote]
try the live cd first and use this option at the boot prompt ```
live acpi=off
```if that fixes the restarting issue when you wan't to install ubuntu enter this option with the install cd at the boot prompt ```
linux acpi=off
```

---

