---
title: "Interpreting a Kernel Panic (Fiesty)"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by Grafster on 2007-03-29
So I've also encountered some version of a Kernel Panic error, probably related to my hardware.

Initially I thought it was bad ram but I've run memtests over the last few days and found a clean stick. The problem replicates with 100% accuracy on both Edgy and Feisty install attempts; however it does _not affect Dapper_.

I can load Memtest off the Feisty CD (or Edgy CD), but any other choice dumps me to the Kernel Panic.

I don't really know if this should be a bug report or what. I've gone through kernel panic threads but nothing seems to match up with the errors I'm picking up.
[The CD I'm using is good, zero checksum errors...]

Instead of trying to type out everything on the screen (with the attendant possibility of errors) I've actually taken two pictures.

20070330(001).jpg shows the bottom half of the screen (the flash makes it hard to see the middle) it has the full code.
20070330(upper).jpg  shows the upper part of the screen and the rest of the error.

Any ideas?
Thanks!

---

### Post by Grafster on 2007-03-30
No ideas?

---

### Post by Grafster on 2007-03-31
So, according to [this thread]("http://www.linuxquestions.org/questions/showthread.php?t=353920"), you look at the code before the kernel panic to try to identify what went wrong.

The previous line says EIP...
(goes off to look at what an EIP is...)

---

### Post by Grafster on 2007-03-31
The alternate CD also doesn't work.

---

