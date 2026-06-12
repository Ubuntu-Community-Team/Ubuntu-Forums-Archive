---
title: "Can't upgrade to Breezy using Live Kubuntu CD"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by bertilow on 2005-10-13
I have Kubuntu Hoary 5.04 installed. It works perfectly.

I downloaded an ISO image of the live CD version of Kubuntu 5.10
"Breezy Badger" - Release i386.

I checked the MD-sum. It was correct.

I burnt the image to CD.

I tested the CD as a live CD. It worked (I got a nice KDE
desktop). I also checked the CD integrity. No errors.

I followed the instructions in "BreezyUpgrade"
([https://wiki.ubuntu.com/BreezyUpgradeNotes):](https://wiki.ubuntu.com/BreezyUpgradeNotes):)

* I installed the meta-package "kubuntu-desktop" (which for some
reason was not installed)

* I opened up Synaptic Package Manager

* I clicked on "Edit/Add CD-ROM".

And I got the following error message:

  "E: Unable to locate any package files, perhaps this is not
  a Debian Disc"

(Should it be a Debian Disc?? I use Kubuntu, not Debian.)

* I tried to add the CD using "sudo apt-cdrom add". That gave the following:

  Using CD-ROM mount point /cdrom/
  Unmounting CD-ROM
  Waiting for disc...
  Please insert a Disc in the drive and press enter
  Mounting CD-ROM...
  Identifying.. [e04c2270ae0b487432e3b89b2b23cf07-2]
  Scanning disc for index files..
  Found 0 package indexes, 0 source indexes and 1 signatures
  E: Unable to locate any package files, perhaps this is not a Debian 
  Disc

And yes, the correct CD is in the CD drive (I have only one CD drive).

Please, what am I doing wrong?

---

### Post by joelito on 2005-10-14
The Live CD is not meant to be used to upgrade/install, you need the Install CD to do that. The commands were ok (AFAIK)

---

### Post by bertilow on 2005-10-14
[QUOTE=joelito]The Live CD is not meant to be used to upgrade/install, you need the Install CD to do that. The commands were ok (AFAIK)[/QUOTE]

OK. Thanks. I'm burning a real install CD right now.

---

