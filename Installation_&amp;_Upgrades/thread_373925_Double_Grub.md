---
title: "Double Grub?"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by dwcone on 2007-03-01
Ok so i've been messing around with ubuntu since vista came out (better time then any right?) and i've run into a problem. I have an HP dv8000 laptop with a dual 80gb SCSI setup (so 160 gb total) and I have it partitioned with 3 main partitions sda1 (windows) sda2/3 (ubuntu) and sdb1/2(kubuntu). Kubuntu is my main partition and I was going to mess around with beryl on my ubuntu partition. They were installed in the order: windows, kubuntu, ubuntu. I now want to remove my ubuntu partition but I found that for some reason the grub that kubuntu installed wasn't recognized and ubuntu is now running grub through it's menu.lst. I may be just ignorant but how do I remove the ubuntu partition. I can't just reformat that partition because that's the grub that's booting right? Any help would be appreciated.

---

### Post by confused57 on 2007-03-01
> **dwcone said:**
> Ok so i've been messing around with ubuntu since vista came out (better time then any right?) and i've run into a problem. I have an HP dv8000 laptop with a dual 80gb SCSI setup (so 160 gb total) and I have it partitioned with 3 main partitions sda1 (windows) sda2/3 (ubuntu) and sdb1/2(kubuntu). Kubuntu is my main partition and I was going to mess around with beryl on my ubuntu partition. They were installed in the order: windows, kubuntu, ubuntu. I now want to remove my ubuntu partition but I found that for some reason the grub that kubuntu installed wasn't recognized and ubuntu is now running grub through it's menu.lst. I may be just ignorant but how do I remove the ubuntu partition. I can't just reformat that partition because that's the grub that's booting right? Any help would be appreciated.

You could reinstall the Kubuntu grub to the mbr, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

