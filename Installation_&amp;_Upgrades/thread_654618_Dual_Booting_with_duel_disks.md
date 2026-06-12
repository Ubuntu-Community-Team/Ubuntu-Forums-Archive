---
title: "Dual Booting with duel disks"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by aasteve on 2007-12-31
I have two disk drives.  One is WinXp.  The other with Ubuntu 7.10.  I want Ubuntu as the C: drive and XP as the D: drive.  Can I modify grub to see both drives and offer dual boot?
Thanks. Steve

---

### Post by chewearn on 2007-12-31
> **aasteve said:**
> I have two disk drives.  One is WinXp.  The other with Ubuntu 7.10.  I want Ubuntu as the C: drive and XP as the D: drive.  Can I modify grub to see both drives and offer dual boot?
Thanks. Steve

Short answer: Yes.

Long answer:
Add a stanza for WinXP in menu.lst at the bottom of the file, something like this:

title                   Windows XP
root                   (hd1,0)
savedefault
makeactive
chainloader +1
 map                   (hd0) (hd1)
map                   (hd1) (hd0)

(hd1,0) should be correct, though depends on your exact system set-up.  If this doesn't work, post back with output of:
```
sudo fdisk -l
```

---

