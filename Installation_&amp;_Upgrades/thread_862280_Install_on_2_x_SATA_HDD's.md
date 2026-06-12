---
title: "Install on 2 x SATA HDD's"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by bertles86 on 2008-07-17
Hi folks,

Noob here, I have XP SP3 installed on my primary SATA HDD, just popped a spare SATA HDD in the case. Set BIOS boot seq to CD/XP/Spar, and booted from Ubuntu CD.

Got to partition box in install and it was blank. How do I choose where to install Ubuntu to? 

P.S. The spare needs a format it has junk on it.

Thanks!

Edit: All buttons barring Cancel/Back/Continue are greyed out, on clicking Continue I get - 'No root file system is defined.

Please correct this from the partitioning menu.'

---

### Post by bertles86 on 2008-07-17
Also when the install GUI is loading, the following messages appear:

[279.197569] ata 5.00: revalidation failed (errno=-5)
[314.303408] ata 5.00: revalidation failed (errno=-5)

Am I looking at a corrupt HDD? Why do neither HDDs show?

---

### Post by bertles86 on 2008-07-18
Bump

---

### Post by confused57 on 2008-07-18
One thing you might try is pressing F6 at the live cd initial boot screen, then add all_generic_ide to the end of the boot options line, then press enter.

Another possiblity is to go into your bios setup and change the SATA controller from AHCI to IDE or vice versa.

There may be some other boot parameters that could help with recognizing your hard drives...

---

### Post by bertles86 on 2008-07-18
Thanks I'll try that now.

---

### Post by bertles86 on 2008-07-18
Worked a treat cheers pal. The F6 bit.

---

