---
title: "specs for an old desktop to run ubuntu?"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by Bmarceld on 2010-08-09
specs for an old desktop to run ubuntu?

---

### Post by CPL2010 on 2010-08-09
Just installed 10.04 on this config for my 6 year old.

   17 inch monitor
  512 of Ram
  20 gig drive
  1.0 Ghz P3
  Ancient S3 video card, I think it&#8217;s got 4-8 megs on it.
  DVD/RW drive
  
All he uses it for is flash games, SNES emulation and some of the educational stuff for kids in the repositories.

It took an hour to install and it takes awhile to boot, but he doesn't seem to care.  It was the same think with Windows XP.

I should also mention it's a frankenstein machine made from my extra's pile of crap from work.

---

### Post by snowpine on 2010-08-09
The hardware requirements for Ubuntu are very well documented:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by efflandt on 2010-08-09
Old is a relative term.  Do you mean from this century or pre-y2k?

The most important thing may be RAM.  256 MB is marginal, 512 MB or more is best.

I am relatively new to Ubuntu (discovered it a week before 9.10 was released) and the oldest PC I installed it on was a pre-y2k Pentium III 550 w/512 MB RAM.  Although, that was Qimo for kids (based on Ubuntu 8.10, upgraded to 9.10).  It did not do flash video well, but was fine for the kids (educational) games.  Because its BIOS was pre-y2k, I had to use **acpi=force** and for it to power down completely I had to use **lapic** kernel boot parameters.

When I had to borrow RAM for another older laptop, a low end laptop from 2004 worked fine with 512 MB.

There may no longer be "accelerated" video for older video cards, but most should work with default drivers (might need **nomodeset** kernel boot parameter).  Things like DVD may work fine, but on-line videos may have a low frame rate.

There are other Linux versions for older slimmer hardware with less RAM.

---

