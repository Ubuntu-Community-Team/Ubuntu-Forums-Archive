---
title: "Fakeraid / Sata / Grub / Dual Boot Issue"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by Steveha1 on 2006-06-06
Have been trying for many months to install Ubuntu but cannot seem to get past the install part, though not for lack of trying.  Can anyone give the the simple fisrt steps that I need to do.

I have Two Sata drives that are raid 1 and contain Windows XP. I have another Sata drive (not part of a raid) that is for Dapper.  In my Bios the Sata mode is set to Raid - guess that is the 'fakeraid'.

When I install Dapper it sees 3 disks so I guess it is not able to see the Raid disks as one drive.  Anyway, when I get to installing Grub it detects that I have Windows XP but shows it once for each of the two Raid disks.  If I have the raid as my first boot disk then it goes straight to xp, if i have dapper as my first boot disk then grub hangs.

However, if i set the Sata mode to ACH and dapper as my first boot disk i can start dapper but grub does not see xp.

Can anyone give me the simple step that i need to take to keep my Sata mode set to raid, and be able to have dapper on the other sata drive and grub can offer me choice of OS.  Hoping for you kind assistance.

Thanks

---

### Post by Vati-Khan on 2006-06-06
what chipset are you using

which "raid-controller"

and is the necessary module loaded? (sudo lsmod)

---

### Post by Steveha1 on 2006-06-06
Hi there, many thanks for your reply.  I have the Intel 82801FR Sata Raid Controller.  Being new to Linux I cannot say what modules are loaded!
Thanks your kind assistance.

---

### Post by Steveha1 on 2006-06-07
Is it dmraid that i need to install?  if so, how is it done in simple terms.

---

