---
title: "Update packages on Live CD"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by superhac007 on 2008-02-18
Does anyone know the process of updating the packages that get installed when installing a new system.       I am constantly installing new machines on 7.10 that require 189 package updates.  I have been doing it manually by using a connected machine and then copy the updated packages to an external harddrive but its a pain.

I would like to update the packages that get installed from the Ubuntu cd.  I have found numerous guides to making custom live cds, but I don't want to update the live system.  I want to update the packages that get installed during the installation process.

Thanks.

---

### Post by DrewMac on 2008-02-18
I don't think that's possible since the CD installs the same things as the live environment. So if you update the live environment, shouldn't that update what is installed?

---

### Post by superhac007 on 2008-02-18
That I don't know for sure.  But I would assume the install is built from binary packages using a manifest file.

I know theres got to be a way to do it.  I was just hoping that someone else had already documented it so I wouldn't have to hack around the live cd.

Thanks for your help.

---

### Post by superhac007 on 2008-02-18
> **DrewMac said:**
> I don't think that's possible since the CD installs the same things as the live environment. So if you update the live environment, shouldn't that update what is installed?

Yep you were right.  I went through the process of creating a custom live image to the point of chrooting.  Then I updated the packages with the new packages and created a new iso.  It worked like a charm. 

Its been so long since I packaged a distribution that I complely over looked the side benefit of using live images for installs.  There are no packages.  It  just uncompress the live system on to the hard drive.   I also did quite a bit of reading after words on the live building process and casper.  Quite impressive stuff....

Thanks again for your help.

---

