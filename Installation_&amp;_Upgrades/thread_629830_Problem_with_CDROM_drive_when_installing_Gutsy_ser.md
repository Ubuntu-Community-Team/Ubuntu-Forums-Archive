---
title: "Problem with CDROM drive when installing Gutsy server"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by murrellr on 2007-12-02
I have an IMB eServer xSeries 350 with quad 700MHz Xeon processors.  When I try loading Gutsy V7.10 server from a CD, the loading fails after a few minutes with a fatal CD-ROM error.  When I run the CD test, it fails after a file or two with an md5 checksum error.  Sometimes its the first file, other times its goes a few files, but never more than 1% of the test.

Through trial and error, I have determined its not the CD (I burned multiple CD with images from different mirrors with different devices, and the CD will boot and pass on my HP Pavillion), and its not the CD-ROM drive (I've swapped out the drive).  I can also boot and run V6.06 server without error.  It seems that the hardware drivers in Gutsy do not like the IBM hardware.

I'm running on V6.06, but I would like to upgrade to the latest.  Searching the forums didn't turn up a problem similar to mine.  Any ideas as to what may be wrong and how to correct it?

---

### Post by Kleenux on 2007-12-02
Before getting into the harsh of finding and providing the right drivers (provided that it is indeed the problem), try the Alternate distro from the same Ubuntu download page. I has a similar problem with Feisty that the alternate cd fixed.

---

### Post by murrellr on 2007-12-07
The alternate CD did not work.  I'll stick with V6.06 for now.  I may try an internet install, but that will have to wait.  I need to get the server up soon.

---

