---
title: "Ubuntu 7.04 Server, Int 14 Boot Error (Virtualbox)"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by benton on 2007-09-11
Hi there, I installed Ubuntu 7.04 Server in Virtualbox 1.5. Installation went fine, but when it rebooted I got this error:

Int 14: CR2 c10000000 err 00000002 eip c03f3c3e CS 00000060 flags 000100006
Stack: 373c0046 00000000 ffffffff c0490000 00001400 00000080 004000000 ffffff80

Any ideas?

Thanks!

---

### Post by benton on 2007-09-11
Solved by installing the generic kernel:

[http://www.virtualbox.org/ticket/289](http://www.virtualbox.org/ticket/289)

---

