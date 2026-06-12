---
title: "Ubuntu, Win XP, &amp; SATA"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by xitshsif on 2005-06-19
I currently have XP installed on my single hard drive, which happens to be SATA.  My single optical drive is also SATA.  I'm definitely interested in installing Ubuntu, either on a new partition on my drive, or I could always buy a second hard drive (would have to be PATA).

I've heard there can be issues with SATA, so anyone have any ideas how tricky it'd be to install Ubuntu while keeping my XP installation intact?

Just trying to see what I might be getting myself into here...

---

### Post by cwaldbieser on 2005-06-19
When I first got my PC, it had a single SATA drive with WinXP as well.  It was my intention from the start to wipe it off and install Debian on it (this was a 2.4 kernel).  Well, much to my surprise, it couldn't recognize the hard disk, and that is when I first learned about SATA drives and compiling support for them into your kernel the hard way.  I eventually got Woody running on a partition on the SATA, but it was so troublesome with all the hoops I had to jump through, I eventually just put a small IDE drive in the case and installed various distros on that.

When I heard about Ubuntu Warty, I gave that a try and tried installing it on my SATA.  Worked like a charm the first time.  I migrated to Ubuntu soon afterwards and haven't looked back.

---

