---
title: "&quot;No installable kernel&quot; during alternate CD install"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by twin_57103 on 2008-03-27
I'm trying to dual-boot a brand-new machine with Ubuntu 7.10.  I'm running an AMD Phenom 9500 (quad-core, 2.2 GHz) with 4 Mb RAM and an EVGA GeForce 9600 GT video card on an ASUS M2N-SLI Deluxe motherboard. There seems to be a [bug with this video card]("http://ubuntuforums.org/showthread.php?t=733923") that doesn't work well with the Live CD, so I'm trying the alternate disk instead.

I get past partitioning to installing the base system when I get a message that says "No installable kernel was found in the defined APT sources."  I've checked the md5sum on my image and it is correct.  I've burned a second copy (slowest speed possible) and ran the error-checking utility from the disk - everything seems correct. I've found a [thread referencing this problem]("http://ubuntuforums.org/showthread.php?t=3444") on older machines, but I'm not sure how much applies or not.  All of the drives are SATA, including the optical drives.

When I installed Vista, I did it on half of one of the hard drives (both 320 Gb).  I left the other half for Ubuntu.  I used the manual partition editor to set up 152 Gb ext3 for root and 8 Gb for swap (the guided partitioner wasn't giving me the options to use this partition).  I don't mind if Ubuntu ends up on the other hard drive; I just want to get it installed - I can't even run it on a live CD!

One suggestion on the other thread was to use a different video card, but the next best one I have is a PCI ATI Radeon X300/X550 - which ran Ubuntu perfectly until a failing hard drive destroyed my Ubuntu installation.  Do you think it would be worth attempting this card on such a new board?  It might allow me to use a live CD.  It's about the only alternative I can think of.

---

