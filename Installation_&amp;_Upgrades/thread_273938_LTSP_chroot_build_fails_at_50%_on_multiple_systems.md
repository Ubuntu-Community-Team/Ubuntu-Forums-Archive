---
title: "LTSP chroot build fails at 50% on multiple systems"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by keltorsori on 2006-10-09
I've tried a number of different Edgy Xubuntu Alternate builds (including knot 3 and beta and dailies up-to 10/8/06) and Edgy Edubuntu builds. On multiple systems with either system the LTSP server install fails at the Build LTSP chroot step. The system goes through 0%, grinds away for a bit, and then ends up at 50%. After grinding for 2-3 minutes I get an Installation step failure. 
> !! Build LTSP chroot
Installation step failed
An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Build LTSP chroot
I have tried multiple discs on multiple systems. Dell B110, Intel Mac mini, homemade Athlon 2500+ XP. All fail at the same stage. 
I'm about to try with Dapper release 6.06.1, but it looks like either there's some bug in the LTSP distro for both these releases, or I've picked a lot of bad systems.

---

### Post by keltorsori on 2006-10-09
Tried the final 6.06.1 release of Xubuntu alternate and edubuntu, both install fine. Any ideas guys?

---

### Post by keltorsori on 2006-10-14
Bug submitted, bug fixed. Both were missing a package for installation.

---

### Post by sindile on 2007-02-01
I still have the same problem running Xubuntu Feisty Fawn Herd2, but when I try to do a manual install using sudo ltsp-build-client --mirror file:///media/cdrom0 I get this message at the end E: couldn't find package linux-image-386, error: LTSP client installation ended abnormally.

---

### Post by kenlyle on 2007-03-06
I had the same failure of Edubuntu 6.1 that I downloaded today on a VIA CV860A board.

Ken

---

