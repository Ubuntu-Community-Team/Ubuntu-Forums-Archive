---
title: "Help- can't boot windows"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by gj502003 on 2007-07-18
Background:
I set out to setup ubuntu to dual boot on a Dell 620 laptop with win xp.  After running the livecd install, I rebooted.  The grub menu came up and I could boot linux, but I got an error when trying to boot windows.  It turns out, the windows partition was reformatted.  

I purged all partitions from the drive and reinstalled the windows partition from a backup.

Problem: The computer won't boot.  I've tried using fdisk /mbr command, but I get the message that it can't write the mbr.

I don't have my system disks or a windows xp install disk.  I have a complete backup using Acronis True image, but when I reinstall, it won't boot.  I think it is a problem with the mbr.

Any suggestions?

---

### Post by confused57 on 2007-07-18
You could try the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You would need access to another computer to burn a copy...there is an option to "Fix Windows Boot" in SGD.

---

