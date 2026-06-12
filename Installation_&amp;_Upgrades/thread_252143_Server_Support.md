---
title: "Server Support"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by William_the_bookman on 2006-09-06
I would like to install ubuntu on an old Compaq Proliant 5000 server, but I want to check a couple of issues first:

1. Has anyone else installed on such a machine? Any gotchas?

2. This beast has 4 processors. Does Ubuntu come with SMP support "out of the box", or will I need to recompile my kernel?

---

### Post by skymt on 2006-09-06
1. I don't experience with that machine in particular, but it should work. Linux drivers tend to lag behind Windows for cutting-edge hardware, but older stuff should almost always work.

2. The default kernel is single-processor. You can install an smp kernel once Ubuntu is installed ('sudo aptitude install linux-686-smp').

---

### Post by magicfab on 2006-09-18
Ubuntu 6.10 will have new packages that obsolete linux-686 / linux-686-smp:

linux-generic
linux-image-generic

---

