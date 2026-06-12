---
title: "boot of ubuntu hangs with either install or livecd"
date: 2013-07-08
forum: Installation &amp; Upgrades
---

### Post by deeppow on 2013-07-08
Trying to install 12.04.2 64bit.  I'm using Nvidia cards (booted with nomodeset) but took them out to try an old Radeon 4890 card.  Same result in that part way through either situation (the install or starting livecd), it hangs, i.e. part way through coloring the dots.

I'm running 3 SSDs (one with Win7 64) on it that is my normal boot OS and the other 2 are apps.  Also a RAID of HDs with data etc.  Took the 2 SSDs and the RAID off, leaving only the one SSD where I wanted to install Ubuntu ---- same result.

I've tried a bunch of stuff but nothing works.  Suggestions?

---

### Post by dino99 on 2013-07-09
grub is very sensitive (too) : for example, a borked journal or some broken inodes can stop it. So check each device and the raid

---

