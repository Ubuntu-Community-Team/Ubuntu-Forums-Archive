---
title: "New on the block - how to triple boot ?"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by radiospock on 2007-03-03
I already have a dual boot system with XP and Vista, and have no experience of Linux at all. Can someone advise me if it is safe and feasible to install Ubuntu into this system and the best way to go about it. I have three physical hard drives, each of 250 GB. the first is partitioned int two equal parts both NTFS and has XP and Vista on it. The second is in the form of one NTFS partition with my important documents and  pictures on it. The third is partitioned into two FAT 32 and has my backups on one half, whilst the other half is spare. I would like to put Ubuntu on this spare partition. I would welcome some input on this. I have read all the posts on the topic of triple boot on this site, but none  seem to cover my special circumstances.

---

### Post by ingo on 2007-03-04
Well, I don't dual boot, but your safest option would be to disconnect the first two disks and install ubuntu onto the empty partition of the third disk with grub, the boot loader, in the mbr of disk three. Now tell the windows boot loader to point to the mbr of hard disk three and you should have a proper triple boot system.

HTH

---

### Post by radiospock on 2007-03-05
Thanks for the advice. I did what you suggested and Ubuntu installed fine on the spare drive. After reconnecting the Windows drive XP and Vista boot as normal. I'm not quite sure how to add Ubuntu to the Vista boot loader though. I have a copy of VistaBootPro but don't know where I go next.

---

### Post by ingo on 2007-03-05
oops, I'm sure you're in the wrong forum for that here :) try this link [http://www.flexbeta.net/forums/index.php?act=ST&f=48&t=8373](http://www.flexbeta.net/forums/index.php?act=ST&f=48&t=8373)

---

