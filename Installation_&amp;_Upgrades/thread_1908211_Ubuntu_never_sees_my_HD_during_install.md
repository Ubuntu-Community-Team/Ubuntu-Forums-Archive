---
title: "Ubuntu never sees my HD during install"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by vt.dave on 2012-01-13
Hi Everyone,

For reference this is on a Shuttle SX58H7 PRO.

I can boot off of the CD or a USB stick (only with acpi=off) and when it comes to the system check screen it never says I have 4GB Free.

I have tried 2 separate HD's, a 240 gig SSD and a 1TB regular HD, but neither are ever recognized.

I have tried IDE, AHCI and RAID in my BIOS for IDE settings and have the drives plugged into a 6 Gb/s sata port on my Mobo.

Does Ubuntu look for a specific SATA controller during intall? Why can't I get Ubuntu to see my HD?

Any help is appreciated!
-Dave

---

### Post by Mark Phelps on 2012-01-13
Most likely, it is the 6Gb/s SATA port.  I've seen lots of threads from folks with similar problems.

Try connecting the drives to an older 3Gb/s port instead.

---

### Post by varunendra on 2012-01-13
> **Mark Phelps said:**
> Most likely, it is the 6Gb/s SATA port.  I've seen lots of threads from folks with similar problems.

Try connecting the drives to an older 3Gb/s port instead.

So does it mean Ubuntu is unable to use a 6gb/s SATA port? That would be a letdown and a surprise to me (not that I've ever used a 6gb/s port before ;))!

As a side note, I've recently experienced that although Ubuntu Live can see and use a drive on a RAID card, it does not list it when we proceed to the installation step (it was a single-drive strip/RAID-0 setup). So I think it's worth making sure that the port is not configured for a RAID array.

---

### Post by vt.dave on 2012-01-13
> **Mark Phelps said:**
> Most likely, it is the 6Gb/s SATA port.  I've seen lots of threads from folks with similar problems.

Try connecting the drives to an older 3Gb/s port instead.

You were 100% correct.  Ubuntu installed on my HD no problem after that.  Now I'm going to try the SSD instead of the baracuda.  Hopefully that works as well.

---

