---
title: "Alternate installation with preseed- only reliable with newly burned CD?!"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by NigO on 2007-11-05
I have been trying to produce a custom alternate installer to install ubuntu (Dapper) on multiple machines using a preseed file.

When I create the ISO and burn the CD, the installation works perfectly, every time.  If I try to reuse the CD on that or another machine, it fails at "installing packages".  The progress bar locks at 17%, and the display usually reads "installing lvm2" or "installing xorg".  Occasionally (maybe once in ten tries at best), it works.

Other console screens show no obvious error messages, I can go in to the busybox shell but there are no obvious errors in the logs.

I have tried burning the CD on 3 different machines, at speeds from 8x to 24x, and tried different media brands, and tried the same installation on different hardware- no difference.  I have also tried swapping between installation CDs, powering off the machine completely at the isolator between installations, no luck.  The CD shows no signs of damage (initially suspected it may have been scraped by the drive during the first installation)

On the 'faulty' CD, I can select the original alternate install (not preseeded), and it completes successfully.  Every time.  100%!

What happens at the '17%' stage of package installation which might cause this, but particularly on a preseeded installation and apparently not with a newly burned CD?

Nigel

---

