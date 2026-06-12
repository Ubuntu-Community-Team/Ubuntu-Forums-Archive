---
title: "GRUB Stage 2 Error"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by Xabora on 2008-01-30
Well here is a new one.


Grub upon boot now gives me an error as it goes into stage 2.

I've read this has to deal with how Grub interprets the drive locations.
So my USB HDD location '/dev/sda' becomes '/dev/sdd'?

Thanks

---

### Post by doddo on 2008-02-02
Hello!

This is a nasty problem!

You are correct in the sense that grub probably tries to load stage2 from wrong disk

Have you changed the disk layout since installation??

are you booting from external disk??

If not, is there somewa for you to get to the grub prompt, like removing disks or stuff like that?

---

