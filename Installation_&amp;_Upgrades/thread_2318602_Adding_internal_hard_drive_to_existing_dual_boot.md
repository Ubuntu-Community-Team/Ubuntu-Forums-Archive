---
title: "Adding internal hard drive to existing dual boot"
date: 2016-03-27
forum: Installation &amp; Upgrades
---

### Post by flyingsolo on 2016-03-27
I have 14.04 and Win 10 sharing a large internal drive, 2TB. I'd like to add an extra internal HDD which has stale data from another, old computer. I plan to wipe it and use it for backups of critical files.
When I add it, I don't get the usual screen to choose which OS to boot. Just blank screen.
Probably a problem with boot order? Need some suggestion of how to proceed.
Thanks.

---

### Post by oldfred on 2016-03-27
UEFI or BIOS?
And what SATA port? Always best to use SATA ports in order or first drive SATA0 will then be sda.

I skipped a port. Then flash drive when plugged in as sdf, on reboot would be sdb changing all my other drives. System still booted as it use UUIDs, but anything using device like /dev/sdb was then wrong.

---

### Post by flyingsolo on 2016-03-27
BIOS.
Original drive is in SATA3 and I first tried the new drive in SATA4 which is when I got nothing happening on restart.

---

### Post by ubfan1 on 2016-03-27
This second HDD was not added with a disk caddy (replaces the DVD) was it?  I had trouble booting off any hard disk when I added the caddy, since when grub froze when it accessed it (light turned on and everything froze).  Grub would run off a USB before the HDDs in boot order, and I could then boot a release on the caddy, but found that unsatisfactory.  That was an 2006 HP/Compaq, with an IDE/SATA caddy.  I haven't tried this yet with a straight SATA/SATA caddy.

---

### Post by flyingsolo on 2016-03-27
No, new drive just put in one of the open bays for HDD's and plugged to SATA and power.

---

### Post by ubfan1 on 2016-03-27
Try switching the disks?  May be the easy fix.

---

### Post by Dennis N on 2016-03-27
This may work:
Since it has old data, boot into live USB and create new partition table and a partition on the 2nd drive. Exit from live USB, and restart.

---

