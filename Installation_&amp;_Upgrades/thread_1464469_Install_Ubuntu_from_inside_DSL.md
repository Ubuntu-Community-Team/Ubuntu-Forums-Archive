---
title: "Install Ubuntu from inside DSL?"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by chappajar on 2010-04-28
I'm trying to install Ubuntu to a laptop for a relative.
Through my own impatience I accidentally damaged the data on the first partition on the hard disk, which wouldn't matter except that the laptop refuses to boot from most CDs.

It won't boot a Win XP install disk (despite the fact that I've installed Win XP on it from the same disk in the past).

Immediately after I wrecketd the first partition it would boot one of Ubuntu 8.10, 9.04 or 9.10 (I forget which version, and it only worked after I downloaded and burnt a fresh copy, wouldn't work with the copy I already had) but not the other two, and won't boot any of them now.  When it did boot the Ubuntu livecd it would crash a short while after I tried to install. 

It will happily boot into DSL from a live CD.  It wouldn't boot a GParted live cd before, but will now...?

So I'm a bit stuck.  How do I go about getting Ubuntu installed on the first partition.  BTW there is data on the second partition that I can't allow to be damaged or deleted.
The laptop is old, and won't boot from USB.

I'm guessing my best bet is to install through DSL?  I can't open the CD drawer once DSL livecd is running(! Is this normal?) and DSL doesn't find either of the two hard disk partitions, but I can mount an external hard disk in DSL.
Can I use this to install Ubuntu (or at least get the install started, if it crashes again I'll deal with that problem then), and if so, how do I do it?

---

### Post by Bachstelze on 2010-04-28
You can (really, should) use debootstrap for that:

[https://help.ubuntu.com/8.04/installation-guide/i386/linux-upgrade.html](https://help.ubuntu.com/8.04/installation-guide/i386/linux-upgrade.html)

---

### Post by chappajar on 2010-04-28
Thanks Bachstelze, I'll try it, but I'll have to get the laptop connected to the internet first.
If the worst happens, and I can't get online, what are my options?

---

