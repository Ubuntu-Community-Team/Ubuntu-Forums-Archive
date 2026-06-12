---
title: "What is the default file system?"
date: 2004-11-30
forum: Installation &amp; Upgrades
---

### Post by dishbert on 2004-11-30
I installed Ubuntu manually, and selected ReiserFS as the / file system.  I'm now trying to build a new vanilla kernel and I'm having problems that I think might be related to the file system.

If you select "Automatic" to format the whole disk when installing, what file system does Unbuntu install?

---

### Post by amoser on 2004-11-30
ext3


~Alan

---

### Post by dishbert on 2004-11-30
Thanks Alan, that's what I expected.  After I install the new kernel I only get a black screen when I try to boot into it, and when I boot back into the old kernel I now see a "looking for ext3 file system" message before it loads.

So..........I guess I could reinstall Unbuntu with the ext3 file system, or compile ext3 into the new kernel?  Is that an option with menuconfig?  I didn't notice it.

---

### Post by dishbert on 2004-11-30
Opps, what I meant to say was that I could compile Reisfers into the new kernel.

---

### Post by jdodson on 2004-11-30
you would have to download the kernel sources which are not included on the cd, its kind of a pain, i had to do that once, i really think they should include to sources on the cd.  though i can understand why they might not as most people would never use it and the headers are good enough for most people.

---

