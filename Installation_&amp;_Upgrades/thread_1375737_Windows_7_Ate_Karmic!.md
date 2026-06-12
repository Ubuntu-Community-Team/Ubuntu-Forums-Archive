---
title: "Windows 7 Ate Karmic!"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by morningcrafter on 2010-01-08
This is unacceptable.

I've been happily running Karmic for the past few months and Ubuntu for the past 6 with few problems. I decided to dip back into the (pirated) Windows world again recently, however, in order to properly format my Sony Walkman.

**ENOUGH PREAMBLE.**

I installed Windows 7 onto the unallocated 150GB space on my 250 GB hard drive with no trouble. But, when I restart my computer it goes directly to Windows and pretends that I have no Ubuntu partition at all.

I realize that this is because Windows doesn't like GRUB and really hates GRUB2, but I can't seem to fix this. _I downloaded the latest release of Easy BCD which gave me a promising screen upon start up where it allows me to select "Ubuntu" instead of "Windows 7" but then it goes to a GRUB command screen. What do I do here?_

---

### Post by darkod on 2010-01-08
Forget EasyBCD, you shouldn't have even tried it (although some people here advocate it). Just reinstall grub1 (for ubuntu 9.04 or earlier) or grub2 for 9.10 as per the instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Win7 didn't eat anything, just the windows bootloader overwrote grub on the MBR.

---

