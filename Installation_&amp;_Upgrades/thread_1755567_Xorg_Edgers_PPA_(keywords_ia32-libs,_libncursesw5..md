---
title: "Xorg Edgers PPA (keywords: ia32-libs, libncursesw5.so.5.7)"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by 3602 on 2011-05-11
I decided to enable the Xorg Edgers PPA through Ubuntu Tweak. Probably not a good idea.
So new updates. Everything installed fine except for the new *ia32-libs* which, when attempting to install/upgrade, gives:
```
trying to overwrite '/lib32/libncursesw.so.5.7', which is also in package lib32ncursesw5 5.7+20100626-0ubuntu1
```
So naturally I *sudo synaptic* and attempt removal of the *lib32ncursesw5* package. This is undoable because it would bring many many other packages away with it (such as *acpi *and *glx-dock*, even *firefox*).
Now I got PPA-purge and downgraded everything. Things are fine right now but the question is this:
1. What is that error? When Googling I came upon a Romanian forum. Translated but didn't help. Launchpad has similar errors and all of them are on 64-bit systems, as I am.
2. Is this going to happen any time in the future?
3. How do I solve it?

Thank you very much.

---

### Post by 3602 on 2011-05-12
Bump.

---

### Post by 3602 on 2011-06-03
OK as this just happened again, this is going up.

---

### Post by 3602 on 2011-06-04
Bump.

---

### Post by UaHummer on 2011-06-05
I have this problem too...

---

### Post by 3602 on 2011-06-06
Bump.

---

### Post by Spade12 on 2011-06-28
I have the same issue.

---

### Post by 3602 on 2011-06-28
Oh hey it's bumped.
So uh, I have since done a complete re-installation of the system. 
**The problem is caused by installing WINE *before* the new ia32-libs.**
The way around it, I do not know. I only know of the cause because after the installation, I turned on Xorg Edgers PPA before installing WINE. You *may* be able to solve this issue by fully purging WINE.
I cannot mark this SOLVED since re-installing the system is not a "solution".

---

