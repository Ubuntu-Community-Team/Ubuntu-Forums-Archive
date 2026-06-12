---
title: "URGENT: can the filesystem check on Install be terminated?"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by RelativelyQuantum on 2008-03-14
All:

A big problem. I need to terminate the filesystem check on the Gutsy install while it's attempting to build an unallocated partition on a 320 BG HDD. When I click "quit" it gives my the filesystem damage warning. Since it's only checking now, will it actually cause damage?

HELP!!!!

---

### Post by jdong on 2008-03-14
Yes, terminating the filesystem check could cause filesystem damage, as any errors found on the filesystem are fixed in "stages". Interrupting this process could cause your disk to be in such an inconsistent state that even future runs of the filesystem checker won't be able to repair it.

---

