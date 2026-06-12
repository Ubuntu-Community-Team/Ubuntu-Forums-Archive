---
title: "Live CD completely fails to function"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Levant on 2007-10-24
As the title suggests, my Live CD can't really do much of anything. No matter the option I select, it shows the little orange bar moving back and forth under the ubuntu logo, then dumps me in some kind of Debian "ash" terminal leaving me to fend for myself. Understandably, this means all I've managed to accomplish since release has been one massive headache.

The checksums are good. I burned the 7.10 i386 ISO on two different CDs using two different burners at 4x (nice and slow) speed. The verification process comes up clean. The only hint I'm getting is by disabling the quiet and splash in the Live CD when I try to do something. Right before it dumps me into the staggeringly unhelpful terminal environment, it gives me about a bazillion messages that read something along the lines of "I/O Error. fd0. Sector 0". Over and over. That can't be a good thing. For the record, this is my first time trying to install Ubuntu onto a SATA drive (that's the only thing in my PC these days).

I'd prefer to get this solved with haste, my increasingly buggy Windows is increasingly unable to meet my needs. I can't be pissing the days away on stupid installation issues. I'd give 7.04 another shot if it weren't for the fact that I *need* that write to ntfs functionality 7.10 has nicely packaged with it.

---

### Post by rsambuca on 2007-10-24
If Feisty worked for you, all you have to do is install ntfs-3g and ntfs-config to get read/write to ntfs drives.

---

### Post by Levant on 2007-10-24
> **rsambuca said:**
> If Feisty worked for you, all you have to do is install ntfs-3g and ntfs-config to get read/write to ntfs drives.

Well it worked back on the old IDE setup. This is the first time I've tried to put any linux on SATA.

---

### Post by rsambuca on 2007-10-24
It shouldn't make a difference, so I am not sure what the problems are.

---

### Post by Levant on 2007-10-24
> **rsambuca said:**
> It shouldn't make a difference, so I am not sure what the problems are.

That was my thinking too. No clue as to what that error message I posted is about?

---

