---
title: "Making a shared area"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by kooia on 2010-03-13
I have windows xp professional 32 bit.
I want to install ubuntu 64 bit.
 
Is there a way to make a shared area?  And how?

---

### Post by oldfred on 2010-03-13
You just need to make a partition for the shared data that is NTFS. Older directions may still say FAT but your need to use NTFS now. If you understand partitions you can create them in advance with gparted and use manual install. The standard install just shares space with windows and Ubuntu's root & swap partitions, but you can still create additional partitions later if you have not used all 4 primary partitions or 3 primary and one extended with many logical partitions. Be sure to defrag(twice) and houseclean your XP partition before shrinking it.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

