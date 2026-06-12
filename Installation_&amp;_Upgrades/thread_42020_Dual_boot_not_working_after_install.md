---
title: "Dual boot not working after install"
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by hkymre on 2005-06-15
I have XP Home in my first primary partition & have installed Ubuntu into a logical partition behind.

Grub should have gone into the mbr

When the Pc rebooted to finish the ubuntu installation it boots straight into XP.

How do I get ubuntu to boot?

---

### Post by frodon on 2005-06-16
Do you install XP and ubuntu on the same disk ?
if yes, maybe the grub is badly installed, if you want to re-install your grub you can do that : [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)  (I think live CD method is easier)

---

### Post by hkymre on 2005-06-16
Found the problem - I have two hard drives
One is an ide, the other SATA. XP and ubuntu are on the SATA drive.

Looks like grub has installed on the ide - changed the HDD boot order in bios and grub comes up. Can now boot unbuntu but XP fails.

I'll try and reinstall grub to the SATA, change the HDD boot order and try again.

Cheers

---

