---
title: "Install Issue with Ubuntu 18.04.1 and an AMD Radeon HD5450 in an Optiplex GX620"
date: 2019-02-10
forum: Installation &amp; Upgrades
---

### Post by dstadnick on 2019-02-10
I should start by saying that it is my understanding that the drivers for this particular video adapter have been in the kernel for some time and the install behavior is different depending on whether the hard drive has been wiped clean or has a previous install on it.
                                                  
So – the issue, when I attempt to install Ubuntu 18.04.1 on a wiped clean drive with the HD5450 installed, the installation goes to the boot live only screen.  The Install Ubuntu option is not present.  If I install the OS from Live, the install hangs.  So, the install fails whenever the HD5450 is present and the drive has been wiped.
 
Interestingly, if I remove the card, the install completes successfully. Then, if I install the HD5450 (on first boot or otherwise – doesn’t matter) the OS boots successfully and uses the HD5450 as the primary video adapter.
 
When the drive has _not _been wiped clean and has a previous install of Ubuntu 18.04.1 then the install proceeds normally, unlike when the drive has been wiped.

---

