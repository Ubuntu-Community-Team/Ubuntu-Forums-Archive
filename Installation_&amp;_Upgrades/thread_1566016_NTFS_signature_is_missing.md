---
title: "NTFS signature is missing"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by jabrown65 on 2010-09-01
I am ~intermittently~ getting an error during boot: "NTFS signature is missing / Failed to mount '/dev/sda1': Invalid argument..."

The SATA hard drive in question seems fine. I have disk checked it thoroughly under Windows which found no errors, and it performs flawlessly when mounted in Windows or Ubuntu. It is only a few months old. When it mounts under Ubuntu it works fine, but for some reason it often doesn't mount during boot up. Usually it mounts on the 2nd or 3rd restart. Or, after the error I get the option to Skip mounting the drive. If I do this it usually mounts fine after boot, but not always. Weird. 

Initially I thought the error was caused by upgrading from Grub (original) to Grub 2, but I have since deleted all of the partitions on the IDE hard drive which contains the operating systems and reinstalled Lucid in a new partition - including installing the Grub2 -, and to my horror the intermittent problem continued!

Any clues? What information should I post (moderate users, so detailed replies please)

John

---

