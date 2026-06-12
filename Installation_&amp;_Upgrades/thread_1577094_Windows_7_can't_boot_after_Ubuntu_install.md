---
title: "Windows 7 can't boot after Ubuntu install"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by Anadon on 2010-09-18
I installed ubuntu on my machine and I can't boot Windows 7 anymore.  I can still access all the files on windows 7, just can't boot it.

---

### Post by Mark Phelps on 2010-09-18
That's not telling us much ...

HOW did you install it:
1) using the Ubuntu installer, in side-by-side, allowing the installer to shrink the Win7 OS partition to make room for Ubuntu
2) Using the Win7 Disk Management utility to FIRST, shrink the Win7 OS partition to make room for Ubuntu, and THEN using the Ubuntu installer to load Ubuntu into the unallocated space
3) Using Wubi, to basically install inside Win7.

Each of the three methods presents different problems and different solutions.

We can't help you without knowing which method you used.

---

### Post by Anadon on 2010-09-19
first method listed, but it's fixed now.

---

### Post by sfoalex on 2010-10-10
How did you fix this? I just installed 10.10 64 bit and I can't boot into either OS now.

---

### Post by Mark Phelps on 2010-10-11
Like the OP, you're not telling us much useful ...

If  you used the first method, that is asking for trouble as it often results in filesystem corruption on the Win7 OS side.  This can usually be corrected by booting from a Win7 Repair CD (or installation DVD) and running Startup Repair three times.

---

