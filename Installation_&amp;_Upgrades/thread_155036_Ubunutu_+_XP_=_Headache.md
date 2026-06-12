---
title: "Ubunutu + XP = Headache"
date: 2006-04-04
forum: Installation &amp; Upgrades
---

### Post by DjKritical on 2006-04-04
Here is how my computer is setup...

IDE1 Primary - 80 GIG (Boot Disk) - Ubuntu
IDE1 Secondary - nothing
IDE2 Primary - CDROM
IDE2 Secondary - 16 GIG - Windows XP
SATA1 - 200 GIG NTFS Storage

Actions:

1. I installed XP on the 16 gig drive
2. I installed Ubuntu on the 80 gig drive

Problems:

1. I can't boot Ubuntu without the 16 GIG Harddisk?!
2. GRUB doesn't show Windows XP
3. GRUB shows up regardless of which hard disk I boot from

............

Can someone tell me where I went wrong?!

:-k

---

### Post by DeusEx on 2006-04-04
somethings wrong with the XP install

for one, I can't figure out why you have it on a HD on the secondary IDE? No wonder XP won't boot, don't expect a neanderthaler to invent rocket-science either!
I am guessing the MBR doesn't work out.

proper way to do it is to have xp on the primary partition on the first HD.
Once XP is booting OK, one can install Ubuntu without problems.

---

### Post by DjKritical on 2006-04-04
I hope this works...

I've taken half a day off work to get my pc going :D

---

### Post by Buffalo Soldier on 2006-04-04
To makes things easier, it is best to have Windows on the first partition of the first harddisk. (first partition in IDE1 Primary)

---

### Post by DjKritical on 2006-04-04
Worked like a charm :D

---

