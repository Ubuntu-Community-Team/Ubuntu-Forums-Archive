---
title: "Installing kubuntu 8.04 on a RAID 5 system"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by fatherkeith on 2008-06-24
I am trying to have kubuntu 8.04 (AMD 64 bit version) be installed on a RAID 5 setup.  My motherboard specifications are the following

ASUS M2N32-SLI Deluxe
NVIDIA nForce 590 chipset
3 320GB Seagate drives
(More if needed by request)


The drives in the motherboard BIOS are setup as a RAID 5 and even POST that way however when trying to install with the alternate CD or the original CD and I cannot get it to see the RAID 5.  It sees the drives as all single drives.  How do I get it to see the RAID 5?  

Currently I have Windows XP Media Center 2005.  It would be great to even have a duel boot but I cannot even do that.  I am new to the kubuntu/ Linux so please be patient.

---

### Post by fatherkeith on 2008-07-02
Here is the answer I was finding.  Having a RAID 5 as a boot RAID does not work.  I tried the fake RAID and the soft Linux RAID. However if the boot partition is a single drive or a RAID 1 then it works just fine.  However you still have to use the alterative CD to set it up.  Once you try it a couple of times even an extreme novice like me can get the general idea.

---

