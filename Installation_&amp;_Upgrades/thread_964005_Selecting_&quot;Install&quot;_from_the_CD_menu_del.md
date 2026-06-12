---
title: "Selecting &quot;Install&quot; from the CD menu deleted my raid array!"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Ryster on 2008-10-30
This could be pure coincidence, but I don't think so.

I thought I would try the new Ubuntu 8.10 64-bit Desktop Edition and see about installing it onto a USB Flash drive.

I downloaded the ISO file from my Windows Vista system and burned it to a CD. I then shut down Vista, and booted from the CD. Then I selected Install from the menu.

I then got the Ubuntu logo and the orange loading bar. This however stayed on the screen for well over 10 minutes, so I gave up, hit reset and ejected the disk to return to Windows.

Unfortunately though, Intel Matrix Storage Manager now says I have no Raid volumes defined, which essentially means my Vista installation is nuked!

Now I was in Windows right before I booted from the Ubuntu CD, so I know the system was fine beforehand, therefore I'm forced to conclude that the Ubuntu CD instead somehow delete my raid volume on my motherboard.

Heres my specs:
Gigabyte GA-X48-DQ6 Motherboard
Intel Core 2 Quad Q9450 Processor
2 x 2gb DDR2 CL4 Ram

Has anyone else experienced the same? If so, does anyone have a fix?

Thanks,
Ryan Spooner

---

### Post by lemming465 on 2008-11-01
It shouldn't have wiped out your RAID configuration, however the Intel "matrix" fakeraid is not currently supported by Linux.  However, I would have expected it to show no drives during the partition phase, rather than mess up the raid config.

---

