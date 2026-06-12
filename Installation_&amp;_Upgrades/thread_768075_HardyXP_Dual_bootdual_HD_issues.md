---
title: "Hardy/XP Dual boot/dual HD issues"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by aphouser on 2008-04-26
System:
Intel Q6600 2.4GHz Quadcore
Asus P5E3 Mobo
NVIDIA 8600 GTS videocard

Issue:
I have XP installed on a SATA HD and a fresh install of Hardy on an IDE HD.  No matter what I do in the bios, I cannot get the linux drive to load if the windows drive is plugged in.

History:
I tried to first do an upgrade from 7.10.  The servers were all busy as heck so I opted to do a reinstall instead.  Downloaded the 8.04 ISO and did the guided repartition of the entire IDE drive.  Afterwards, neither drive would load together, or separate.  The Ubuntu drive would boot into GRUB, but no selection would work.  The Windows drive was looking for a grub that wasn't present (it was on the other drive).  I unplugged the Unbutu drive and ran a FIXMBR on the windows drive in order to get it back to operational.  Next I unplugged windows, and plugged in the Ubuntu drive and did another complete reinstall.

When the windows drive is not plugged in, the Ubuntu drive works like a charm.  However, there is a lot of data I'd like to pull off the XP drive for some testing and I'd like to have them both accessible via quick reboots.

Any suggestions are appreciated.

---

### Post by aphouser on 2008-04-26
I gave it one more go and reinstalled Hardy with both drives plugged in and all seems to be working well.

---

