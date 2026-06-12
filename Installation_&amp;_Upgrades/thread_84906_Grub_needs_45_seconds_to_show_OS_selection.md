---
title: "Grub needs 45 seconds to show OS selection"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by Cet on 2005-11-01
Hi there,
as a beginner I decided to install Ubuntu together with Windows. So far both are working fine but Grub needs more than 45 seconds just to show me the operating systems. How comes that? Did I something wrong during installation? 
I choosed logical partition as Ubuntu asked me during installation. Should I have choosen primary partition instead logical partition? And what can I do right now?

Maybe that gives a hint: 
   Ger&#228;t  boot.     Anfang        Ende     Bl&#246;cke   Id  System
/dev/hda1   *           1       94035    47393608+   7  HPFS/NTFS
Partition 1 endet nicht an einer Zylindergrenze.
/dev/hda2           94048      155056    30748410    f  W95 Erw. (LBA)
Partition 2 endet nicht an einer Zylindergrenze.
/dev/hda5          124561      155055    15369448+   7  HPFS/NTFS
/dev/hda6           94048      124552    15374142   83  Linux

---

### Post by Cet on 2005-11-01
Ok, I found the fault, it is my DVD drive that causes this delay. It is hosted in a bay called Ultrabay by IBM and it can be replaced to put in a 2. battery, a 2. harddisk, a floppy or another optical drive. Well, when I started my Thinkpad after removing my DVD drive grub came almost immediately. So I guess I have to dump this DVD drive and buy another one.

---

