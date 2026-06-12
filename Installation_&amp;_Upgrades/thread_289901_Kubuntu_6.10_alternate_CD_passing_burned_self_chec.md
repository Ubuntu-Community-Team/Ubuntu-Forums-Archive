---
title: "Kubuntu 6.10 alternate CD passing burned self check for you?"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by Neobuntu on 2006-10-31
I think it is broken. Yes, I burned it correctly (several times and as low as 4X).

Does anyone get a good check? That is, burn it, boot it, and select CD verify and it passes?

---

### Post by Neobuntu on 2006-10-31
Can somebody, anybody, run the built in CD check on "Kubuntu 6.10 ALTERNATE" CD (NOT DESKTOP) and give it an OK, or are ALL of them failing?

---

### Post by redpotty on 2006-11-01
I have run the built in CD check for 5.10, 6.06 and 6.10 (desktop, server and alternate) ISOs and all come out OK.  Running the md5sum check returns between 1 and 3 failures on each one.  I have burned ISOs at different speeds from 2x to 8x.  Every installation has hung or crashed at some point, usually "installing software", between 1% and 97%.

Update: This is what I did...

1. Downloaded ISO on hard disk

C:\> md5sum ubuntu-6.10-alternate-i386.iso = 549ef19097b10ac9237c08f6dc6084c6
this matches the md5sum supplied from the mirror.

2. Then burn ISO image to CD-R at 4x using Roxio Easy CD creator

D:\> md5sum -c md5sums.txt

...:OK
...:OK
./install/netboot/pxelinux.0 : FAILED
./install/netboot/pxelinux.cfg : FAILED
...:OK
...:OK

md5sum: WARNING: 1 of 1619 listed files could not be read
md5sum: WARNING: 1 of 1618 computed checksums did NOT match

The .ISO md5sums match and all but 1 of the 1619 files pass the md5sum check.
Are pxelinux.0 and .cfg necessary for a complete install?

---

### Post by Neobuntu on 2006-11-01
Thank you. I think you are seeing about what I am. MD5 of the iso matches but once burned and booted, the CD does NOT pass it's self check.

All I can say it I've burned CD on this drive before with zero problem and I did these burns both via K3b AND Windows with the same bad result.

Unless someone can confirm successful burn and check of the **ALTERNATE**, **K**ubuntu and **6.10** CD then I think we may need to replace this iso that's available on the mirrors.

Conformation?

---

### Post by infoseeker on 2006-11-01
I downloaded and burnt the Kubuntu 6.10 alternate i386 CD and it passed its own self-check.  I haven't updated to Edgy with it yet as I am waiting for the weekend to do that ;)

---

### Post by Neobuntu on 2006-11-01
Hey, thank you very much. Seemed like if it were possible, people would report it so. Now I will re-download the iso and see if it's the same one. If it is, I can now look for the problem on my end (trust me, I know how to burn a CD correctly). The most likely being varying quality of blank CDs on the same spool. Not likely but we'll see.

Any one else NOT getting a OK check and not yet finding the problem?

---

