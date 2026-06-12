---
title: "Error: sil: only 3/4 metadata /dev/sda"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by Carlbc18 on 2010-11-04
Hi All, 

Let me explain the problem.  When i did my initial install of ubuntu 10.04 server i was using a PCI SIL SATA controller, and i chose the hardware raid 1 setup.. After installation i talked it over with a few colleagues and we decided software raid would better suit our needs.  With that being said, I removed the controller and directly connected the disks to the SATA ports on that mobo.  At that point, I re-ran the ubuntu server install going through the manual software raid 1 setup.  After completion during restart I receiver two errors:

Error: sil: only 3/4 metadata  /dev/sda
Error: sil: only 3/4 metadata  /dev/sdb

I assume this is in regards to the hardware configuration with the card, but since the card is no longer installed, and the system was reinstalled i'm having one hell of a time figuring out where this info is stored.  

My software raid1 has been running strong for a couple weeks now without issue, so i'd like to resolve this startup error. Its more of annoyance since the system starts. 

If anyone could help that would be much appreciated!

---

### Post by P4man on 2010-11-04
I think hardware raid meta data is stored on the MBRs, while software raid (mdadm) on partition superblocks. But Im not confident enough to tell you to rewrite the MBRs as I fear doing so may also mess up your software raid.. Is this a RAID 0 or 1 ? If its a raid 1 I suppose you could try one drive at the time, but I take no responsibility if Im wrong :)

---

### Post by Carlbc18 on 2010-11-04
That would make sense! 

This is software Raid 1.

---

### Post by P4man on 2010-11-04
Well, the usual command to remove that metadata is

sudo dmraid -r -E /dev/sdx

however, its quite possible (even likely) that will ruin your existing raid, and it should never be done on a mounted raid to begin with, so youd have to do it from a livecd, en then probably you will no longer being able to boot. You could backup the MBR with dd and restore it if it goes wrong, but if I where you, Id leave it like it is until the day you want to reinstall.

---

### Post by Carlbc18 on 2010-11-04
Yeah I probably won't be doing that on a running system. i'll keep the information for when i need it. I should have removed the raid before uninstall/removing the SATA card - sigh. Live and learn I guess. 

Thanks P4man

---

### Post by P4man on 2010-11-04
Actually, you should just have run the above command (or zero out the MBR) before installing, but hindsight is always 20/20 :)

---

### Post by Carlbc18 on 2010-11-04
HAHAHA good point! Thanks again! The advice is much appreciated!

---

