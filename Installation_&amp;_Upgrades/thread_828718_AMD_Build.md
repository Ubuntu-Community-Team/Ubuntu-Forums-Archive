---
title: "AMD Build?"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by Rhino2 on 2008-06-14
I have an AMD 3000+ socket AM2 Computer and some guy on a forum said that if I installed the AMD build of MythBuntu (MythTV/Ubuntu) that it would run twice as faster.  Is this true?

My friend said that if I installed it, then the apt-get wouldn't work and that linux ubuntu would break my MythTVs and any softwares that I might want to install in the apt-get and I couldn't watch any of my movies and that youtube and anything that uses Flash movie player would break.

Which one is righter?

---

### Post by Rocket2DMn on 2008-06-14
There really isn't an AMD version, just the i386/x86 32 bit version and the AMD64 which is the 64 bit version of Ubuntu.
I don't think AMD 3000+ processors are capable of 64 bit, but you can check with
```
sudo lshw -C cpu | grep width
```
Post back and let me know what shows up.  There are advantages and disadvantages to using a 64 bit install (if your computer is even capable of it).  See - [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by Habbit on 2008-06-14
AM2 socket CPUs are (AFAIK) Athlon 64, Athlon X2, Opteron, Sempron64, etc. which are all 64-bit capable. AMD64 refers to the new architecture that extends the old x86-32, and its common names are x86-64 (linux) and x64 (microsoft), but it's referred to as amd64 (particularly in source files) because AMD invented it, just like x86 can be called IA-32. However, this does not mean and only AMD CPUs implement it: many Intel CPUs are amd64 capable too.

Regarding benefits and disadvantages, the post linked to by Rocket2DMn explains it pretty well; I just want to add this: it is a bit technical, but hopefully understandable.

*«Unlike other 32<>64 bit dichotomies, the transition from x86 to amd64 brings additional advantages, because there are nearly twice as much processor registers available, which a well-designed compiler might be able to use in order to reduce memory accesses. This can highly speed up CPU-intensive tasks such as AV transcoding, number crunching, etc. In other arches such as PowerPC, the 64 bit version has the same amount of registers than its 32bit counterpart, so applications that use 64-bit arithmetic usually run very slightly slower because memory pointers are 8 bytes long instead of 4. This is also partially remedied in amd64 with RIP-relative addressing, which keeps non-indirect references as 32-bit displacements from the current instruction pointer if possible.»*

However, as explained on the post, a 64 bit install may bring some little headaches caused by bigoted software vendors (like Adobe) which refuse to give us 64-bit users an easy way because "there are not enough users", which is clearly a [Catch 22]("http://en.wikipedia.org/wiki/Catch_22").

---

