---
title: "libstdc++5 obsoleted? Need it for running old application"
date: 2010-01-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by autark on 2010-01-17
I'm trying to run Bibble 4 under Lucid, but it needs libstdc++5, which no longer seems to be available via the ordinary channels. What to do?

---

### Post by TerminX on 2010-01-17
Maybe the packages from Debian Lenny would work?

---

### Post by Starks on 2010-01-17
Same problem on my end. I had to use the old Lenny package to run a script for Bradford authentication of my laptop on the university network.

---

### Post by autark on 2010-01-17
I downloaded and installed libstdc++5 from the Jaunty repositories, and this made it possible to install bibble 4. But, it still failed to start, due to the missing .so file. I suppose it's because bibble 4 is a 32-bit application, while my system is 64-bit, so the real dependency is not on the libstdc++5 package but on ia32-libs. 

Then I googled some more and found a solution: download an older version of ia32-libs and extract the necessary parts to /usr/lib32. 

Anyway, I would have preferred Ubuntu not removing obsolete library versions at all. They should be kept for backward compatibility in case somebody needs them. Now, with my manual solution, if a security issue is found in libstdc++5, I will not benefit from security updates.

---

### Post by kahumba on 2010-01-17
I like when people remove obsolete stuff.
But I googled and couldn't find the difference between libstdc++5 & 6, except "6 being a greater number than 5".
What are some of the real advantages of version 6 over 5? Anyone?

---

### Post by howefield on 2010-01-17
Maybe Bibble 5 would play better with newer Ubuntu editions.

---

### Post by autark on 2010-01-17
> **howefield said:**
> Maybe Bibble 5 would play better with newer Ubuntu editions.

Yes it does! But it's still very new so it hasn't got all the features of the old version yet. I think I'll have to stick with both for some time on.

---

### Post by Ibidem on 2010-01-17
Advantages:
libstdc++6 is the newer, maintained one, and has bugfixes, etc.
Disadvantages:
It is ABI and probably API incompatible with the old one; thus, it cannot be used in place of the old one.
As a result, the package and library names were changed.

That's how Linux packages always work...

---

