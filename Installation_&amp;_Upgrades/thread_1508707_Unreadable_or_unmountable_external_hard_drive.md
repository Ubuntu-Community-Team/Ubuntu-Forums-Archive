---
title: "Unreadable or unmountable external hard drive"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by Brandon Hill on 2010-06-13
I upgraded to Lucid Lynx via Update Manager seemingly without a glitch. Then, I realised the system doesn't recognize the external hard drive- a Seagate Expansion USB 2.0 1TB Hard Drive. Is there some command line functions I can cut and paste to get to the contents of the drive? Or is there a known bug and I shall need to wait for a fix?

---

### Post by darkod on 2010-06-13
Doesn't recognize at all or just doesn't auto mount it?

If you connect the hdd and run

sudo fdisk -l

what does it say?

---

