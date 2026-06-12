---
title: "Can not install the restricted packages during instalation"
date: 2004-12-31
forum: Installation &amp; Upgrades
---

### Post by bab on 2004-12-31
Hi,

I downloaded the warty 4.1 iso images downloaded from the main ubuntu website. I tried to install and everything want ok until the kernel should be installed. The I got the error message that linux-386 depends on linux-restricted-modules-i386 and that that package will not be installed. Looking at the cd the .deb is present on the cd but not under main but restricted section.

How can I make ubuntu understand that it should get that package from there instead of aborting the install process?

Regards,
Björn

---

### Post by Rhodan on 2004-12-31
Hi,

I had the same problem as you, it's been posted a couple of times on this forum by different people. Have you checked that the disk is OK by using the testing option on the Ubuntu installer ?

It turned out to be my DVD writer which for some reason Ubuntu didn't like, luckily I had an old cd-rom drive lying around which I used and it installed perfectly. So if you have another drive, try that.

---

### Post by bab on 2004-12-31
I have a NEC DVD writer (ND-3500). Could it be that writer? I have written the cd with that writer and is booting from it. Do you think that it could be that the cd is incorrectly written or the writer cannot read the disk?

---

### Post by alpha on 2004-12-31
Did you also run a checksum program on the ISO images?

---

### Post by bab on 2005-01-01
Yes I ran a check of the image and it reported no errors. I changed to an older cd-player and was able to install ubuntu with the same cd-disk without any problems.

---

