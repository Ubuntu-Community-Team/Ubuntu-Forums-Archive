---
title: "feisty to gutsy upgrade and Pentium D"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by punkybouy on 2008-02-02
My upgrade from Feisty to Gutsy went well except it now only sees one CPU of a Pentium D.  Kernel seems to be the 2.6.22 generic for X86 and X86 64.  Anyone have any ideas?  Thanks in advance.

---

### Post by punkybouy on 2008-02-02
Here is some additional info.

 ls /lib/modules
2.6.17-10-generic  2.6.17-12-generic  2.6.22-14-386
2.6.17-11-generic  2.6.20-16-generic  2.6.22-14-generic

uname -r
2.6.22-14-386

Looks like I am maybe using the 386 kernel when I should be using another?

---

