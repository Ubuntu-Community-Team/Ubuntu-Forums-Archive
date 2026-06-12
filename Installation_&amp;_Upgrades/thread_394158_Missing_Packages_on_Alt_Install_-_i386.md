---
title: "Missing Packages on Alt Install - i386"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by visualnoise on 2007-03-26
After finding out that the 6.10 live cd will not boot on my desktop, I downloaded the alt install iso for i386.  The installation proceeds normally until the kernel is installed.  At this point the install halts and looking at the log reveals that there are missing packages.  I can only continue with the install by choosing the linux-386 image, no others will work.  After proceeding a bit further, I ran into the same problem again with other packages.

I downloaded the images from 2 sources.  They both have the correct checksums for the images.  Both, however, fail the checksums for individual packages when checking the cd through the menu option.  The specific package on which the fail occurs:

linux-image-2.6.17-10-generic-2.6.17-10.33-i386.deb

It looks to me like the current version of the alt install iso is broken.  Can anyone confirm this?  If anyone else is using the current version of that iso and has had luck getting it to work, please post workarounds.

---

### Post by taurus on 2007-03-26
How fast did you burn it?  Try to burn it again except use a slower speed like 4x.

---

### Post by visualnoise on 2007-03-26
I burned it at 12x, on a 52x burner.  I'll give that a go, though I would honestly be surprised if I burned the same error on two different discs.  We'll see soon enough!

---

### Post by visualnoise on 2007-03-26
After burning a 3rd disk, the same package fails the checksum test from the check cd option.  I really think that an incomplete or corrupt package made it onto the cd, though I would love to be wrong.

---

