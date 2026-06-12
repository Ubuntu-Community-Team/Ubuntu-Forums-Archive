---
title: "Live CD does not pick up my partitions"
date: 2013-01-09
forum: Installation &amp; Upgrades
---

### Post by CryoGear on 2013-01-09
My gparted shows my partitions , all of my non mounted ntfs partitions but the instillation shows me nothing. When I click on any of the boxes in the instillation box it freezes(or the center box where my partitions should be showing) and shuts down the instillation. I get the "internal error" message. 

For the record, I'm flying blind here - no windows to fall back on.

---

### Post by fantab on 2013-01-09
First of all check the integrity of your downloaded .iso by using [**MD5SUM**]("https://help.ubuntu.com/community/HowToMD5SUM") check to make sure that you have uncorrupted Ubuntu CD/USB.

---

### Post by darkod on 2013-01-09
If you have used the disk in fakeraid before, it has meta data remains. In that case the installer ignores it to prevent breaking your raid.

This is usually the reason the installer will not show a disk but Gparted shows it correctly.

If this is yuor problem, from live mode in terminal get rid of the meta data with:
sudo dmraid -Er /dev/sda

If that asks you to confirm removal of meta data, it did find it. Confirm and start the install and it should be fine.

Another reason might be some error in the partition table but in that case usually Gparted would have problems showing the disk too.

---

### Post by CryoGear on 2013-01-09
> **darkod said:**
> If you have used the disk in fakeraid before, it has meta data remains. In that case the installer ignores it to prevent breaking your raid.

This is usually the reason the installer will not show a disk but Gparted shows it correctly.

If this is yuor problem, from live mode in terminal get rid of the meta data with:
sudo dmraid -Er /dev/sda

If that asks you to confirm removal of meta data, it did find it. Confirm and start the install and it should be fine.

Another reason might be some error in the partition table but in that case usually Gparted would have problems showing the disk too.

This solved my issue. Thanks!! Never even heard of meta data before this lol

---

### Post by Cheesemill on 2013-01-09
Also bear in mind you already have the maximum allowed 4 primary partitions, you may run into problems trying to create a new one for Ubuntu installation.

---

