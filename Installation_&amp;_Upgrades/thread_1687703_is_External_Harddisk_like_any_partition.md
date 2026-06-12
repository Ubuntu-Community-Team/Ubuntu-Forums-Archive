---
title: "is External Harddisk like any partition ?"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-02-14
Can I used an external harddisk to install program like Netbeans ? eclipse ?
or a database ?

---

### Post by Mark Phelps on 2011-02-14
While it might be possible, it would be very difficult to get it to work.  Why?

Because depending on HOW you install a program, the installer is going to select the target directories -- and not ask you in the process.

IF you install from source, you could experiment with tweaking MAKE files to point to directories on the external drive -- but I doubt that would work.

Stuff installed via .debs is going to install to wherever the packager decided -- most probably, to directories on your internal drive by default.

---

