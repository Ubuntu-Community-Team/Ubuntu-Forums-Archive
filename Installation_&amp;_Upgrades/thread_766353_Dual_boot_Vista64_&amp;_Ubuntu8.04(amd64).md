---
title: "Dual boot Vista64 &amp; Ubuntu8.04(amd64)"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Krokr on 2008-04-25
I have tried to install the official 8.04(AMD64 version). I used the manual rather than guided partition option, as I'd already created some partitions on my fastest disks for root and home. During the installation there was no recognition of the existing Vista64, but other than that everything appeared to go well and I was soon working in Ubuntu, downloading and customising. I noticed that I could see and access my network and the NTFS drives on my machine right away. However, when I rebooted there was no grub menu and it went straight into Vista???? 

My first reaction was that I missed some grub option somewhere, so I repeated the installation, but there didn't appear to be any options I missed? Any help would be greatly appreciated.

---

### Post by Krokr on 2008-04-25
I've just found another thread which highlights problems with installations in mixed SATA and IDE environments and a bug report at [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/14135]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/14135"). I'm guessing that this may be related as my system has a mixed SATA/IDE disk base.

This is really annoying as I'd hoped to migrate away from MS with my new machine, and my experiences on my old dual boot XP/Ubuntu7.1 box had been very positive. Guess I'll have to live with Vista for a little longer.

---

