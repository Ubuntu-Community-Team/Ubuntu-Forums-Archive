---
title: "Adding Linux to WIndows XP"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by osiris2258 on 2007-10-02
I am looking to add Ubuntu to my desktop alongside an XP installation, so I stop having to carry my linux-only laptop all over Pittsburgh. I have several questions, though:

1) I only have room for linux on the 3rd HD, windows completely occupies the primary drive, give or take a few GB I could free up with a partioner (HD 2 is backups). Is this doable? How do I set it up.

2) Is there any way to make all of my files accessible in both OS? Windows is on NTFS and I would like to use ext3 if possible.

3) I have never had to manually set the partition sizing for linux (always just let it format the computer and set sizing itself), how big do the various partitions need to be?

4) What do I need to do to make sure everything functions/continues to function correctly/as good as it gets on windows :P?

Thanks for the Help!!

System Info:
Custom build
AMD Athalon 64 X2 Dual 2.41 GHz (but probably going to use 32 bit linux, 64 bit still kinds unreliable)
2GB Ram
NVidia GeForce 7600 GT
EPoX EP-MF570SLI motherboard

I use a Microsoft laser trackball and keyboard (sucky software, pretty nice hardware), I am not sure if the non-standard devices present a problem. I also use both American and Japanese keyboards.

---

### Post by mikewhatever on 2007-10-02
> **osiris2258 said:**
> I am looking to add Ubuntu to my desktop alongside an XP installation, so I stop having to carry my linux-only laptop all over Pittsburgh. I have several questions, though:

Hm..., linux only laptop, does not make much sense, but whatever.

> 1) I only have room for linux on the 3rd HD, windows completely occupies the primary drive, give or take a few GB I could free up with a partioner (HD 2 is backups). Is this doable? How do I set it up.

Yes, but the probability of booting problems is higher then with one HD. Expect that you might need to troubleshoot a little.

> 2) Is there any way to make all of my files accessible in both OS? Windows is on NTFS and I would like to use ext3 if possible.

[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)
[http://www.fs-driver.org/](http://www.fs-driver.org/)

> 3) I have never had to manually set the partition sizing for linux (always just let it format the computer and set sizing itself), how big do the various partitions need to be?

It depends on the amount of unallocated space available. The bare minimum for root is about 3 GB, and swap is usually about 1.5 the size of RAM.

> 4) What do I need to do to make sure everything functions/continues to function correctly/as good as it gets on windows :P?

Run Ubuntu from the live CD fist to make sure the hardware works. There is really not much more. 

> Thanks for the Help!!

System Info:
Custom build
AMD Athalon 64 X2 Dual 2.41 GHz (but probably going to use 32 bit linux, 64 bit still kinds unreliable)
2GB Ram
NVidia GeForce 7600 GT
EPoX EP-MF570SLI motherboard

I use a Microsoft laser trackball and keyboard (sucky software, pretty nice hardware), I am not sure if the non-standard devices present a problem. I also use both American and Japanese keyboards.

Expect MS hardware to work on MS products only.

---

### Post by osiris2258 on 2007-10-02
When trying to boot the live CD, this happens:

[   38.837558] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   39.016288] Kernel panic - not syncing IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with 'noapic' option
[   39.016337]

What do I do about this?

---

