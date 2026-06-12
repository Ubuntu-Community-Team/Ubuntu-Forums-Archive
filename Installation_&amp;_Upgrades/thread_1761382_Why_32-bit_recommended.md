---
title: "Why 32-bit recommended?"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by jorritTyb on 2011-05-18
Hi, I have another question.

Why does the ubuntu site recommend to download the 32-bit version instead of the 64-bit version? What's wrong with the 64-bit version exactly?

Greetings,

---

### Post by elliotbeken on 2011-05-18
I think the main reason is that 32-bit will run on all computers where as 64 will only run on 64-bit.

---

### Post by vezolmi on 2011-06-04
They are talking about it in [http://ubuntuforums.org/showthread.php?t=1756578](http://ubuntuforums.org/showthread.php?t=1756578)

== Mini-guide ==

 To know if the CPU is of 32 or 64 bits:
a) grep -w lm /proc/cpuinfo
If we see lm in red is of 64 bits. Otherwise is of 32 bits.
b) sudo lshw | grep "description: CPU" -A 12 | grep width
It says clearly what we want to know (after a few seconds).

If the CPU is of 32 bits Ubuntu must be of 32 bits.
If the CPU is of 64 bits it can work in 64 or 32 bits. So we can choose: Ubuntu can be of 32 bits or of 64 bits.

To know if the installed Ubuntu is of 32 or 64 bits:
a) getconf LONG_BIT
It says clearly what we want to know.                                          
b) uname -m
If it shows i686 or i386 it means 32 bits.
If it shows x86_64 it means 64 bits.

---

### Post by geidorei on 2011-06-04
Hi

Ive read that too, bit confusing. What I was told by a a long time Ubuntu user is that the 32bit version is more stable (maybe so in the past?), but Ive got Ubuntu 11.04 (just upgraded) & 10.10 installed on 6 machines, all 64bit installations, and no issues whatsoever.

---

### Post by bjchip on 2011-06-07
Ubuntu may work well enough.  Driver support may however be difficult for the average user, and is difficult enough for knowledgable folk who wander off to do something unusual.  Drivers get written for Windows first, 32 bit linux second and 64 bit linux last.  Means you may not be able to use your joystick or something else, until the folks who are writing things like this catch up.  That's my understanding of the situation anyway.

---

