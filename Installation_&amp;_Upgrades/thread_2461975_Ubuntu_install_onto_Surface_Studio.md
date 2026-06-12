---
title: "Ubuntu install onto Surface Studio"
date: 2021-05-11
forum: Installation &amp; Upgrades
---

### Post by rickticktock on 2021-05-11
I say chaps,
    I'm trying to install Ubuntu onto my Microsoft Surface Studio because I'm tired of notifications to upgrade my Office account, which I no longer want or need.
The MSS uses RAID disk management, which Ubuntu can't deal with. I need to change it to AHCI.
The MSS uses UEFI instead of BIOS. This does not have a convenient way to change the SATA mode, that I can find.
I've tried changing SATA mode in registry editor as advised by various people on my searches, but the changes get set back again when I re-boot. 
All suggestions gratefully received.
TTFN
    Rickticktock

---

### Post by dddman on 2021-05-11
Hi Rick

Its hard to find Linux support for MS products, but there is a 
linux-surface/community here:
[https://gitter.im/linux-surface/community?at=5db765cdef84ab3786b51d44](https://gitter.im/linux-surface/community?at=5db765cdef84ab3786b51d44)

And I know of this:
[https://github.com/linux-surface/linux-surface](https://github.com/linux-surface/linux-surface)

I run the Dell version of a surface pro with 20.04 and most everything worked out of the box, even the touch screen.  I do not dual boot but instead run Ubuntu as a virtual machine.  This allows me to run both (windows/ubuntu) concurrently, switching between the two with just a click.  This is hard on system resources, I run a 4core i5 and 8 gig of ram and would consider that minim requirements, but others have did it on less.  And since this is done with software there is no need to do any disk partitioning.  Thats all I have, good luck and buy a Dell next time :D

---

### Post by rickticktock on 2021-05-12
Hi dddman,
Thank you. I shall follow up
TTFN
Rickticktock

---

### Post by rickticktock on 2021-05-12
No mention of RAID and AHCI, but much talk of a patched kernel. Will that deal with it?
TTFN
Rickticktock.

---

