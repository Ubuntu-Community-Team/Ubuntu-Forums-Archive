---
title: "Duel Booting On Two Drives?"
date: 2004-11-17
forum: Installation &amp; Upgrades
---

### Post by Tarisutan on 2004-11-17
I was able to install Ubuntu on my work computer which happens to have one ide hard drive, which is partitioned. However at home I have one sata drive which windows resides on and I have another ide hard drive which I want ubuntu to exist on. I am able to install it fine however I don't think that grub is being installed in the right place (on the mbr of the sata drive). Is there anyway to fix this, its just been booting right into windows without brining up the grub boot loader.

Thanks, Tarisutan

---

### Post by jdong on 2004-11-17
Set your BIOS to boot from the IDE drive first. GRUB should have a menu entry for Windows already.

---

### Post by ashley_v on 2004-11-17
If you have a rescue disk or something that will let you get into cfdisk then you may want to run cfdisk on the drive and toggle the bootable flag to whatever partition grub is installed on.  Ususally it works better when you just tell grub to install to the mbr that will overwrite your windows mbr.

---

### Post by wallijonn on 2004-11-20
If you have an SATA with WXP and an IDE, disconnect the SATA drive, install Ubuntu onto the IDE, reconnect the SATA and then go into the BIOS to select which HD to boot into (instead of using GRUB). The same would apply if you have two IDE HDs.

---

