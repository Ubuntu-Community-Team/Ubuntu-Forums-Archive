---
title: "[SOLVED] Wrong memory configuration"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by msrk on 2008-01-03
Hi,

I installed Ubunto Release 7.10 (gutsy) on a computer with 1GB of RAM.  However, the System Monitor only finds 242.0 MB.  Consequently the system is swapping quite a bit and the performance is lousy.  How can I get the OS to find all the available RAM?

Thank you,
Marc

---

### Post by ARhere on 2008-01-03
There could be a whole range of reasons for that.

My first thought is you have an integrated video card that uses shared memory.  In other words, it steals part of your system memory for vid use only.

If so, goto your BIOS and reduce the "Shared Video memory" option to 64MB, and your "AGP Apiture" memory to 128MB.

Let me know if this is not the solution.

-AR

---

### Post by msrk on 2008-01-03
Thank you for the speedy reply.  I'll try your suggestion.

In the meantime would it help to know that before Ubuntu Ihad Knoppix which found all the memory without any tinkering?

---

### Post by ARhere on 2008-01-03
hmmm.... not sure.  That is an Operating Systems question.

Does the BIOS lock the memory before the OS see's it, or like other resources, are merely presented for the OS and can be changed as needed.

In short, I don't know that one.  Sorry.

-AR

---

