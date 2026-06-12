---
title: "Uninstalling Ubuntu, without breaking GRUB booter"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by Wisp558 on 2008-03-30
After installing Ubuntu 7.10 on my HP ze4805us pavilion, I realized that my video adapter (ATI, of course) wasn't compatible with Ubuntu, and after looking around, I found that there was no fix that I could use to fix it that was within my skill set. Oh well. I still have Ubuntu on other machines, so I'm about ready to take it off this one, but my question is this: How do I uninstall Ubuntu, and reformat its partitions into NTFS, without breaking the GRUB booter that comes with Ubuntu? Last time I did something like that, GRUB wouldn't load, and I wound up reinstalling windows... Fun. So, how do I take off GRUB and Ubuntu without damaging my capacity to boot windows?

---

### Post by Pumalite on 2008-03-30
Get Gparted Live CD and delete Ubuntu, then fix your Windows MBR with Super Grub.
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
You can use Gparted Live CD to resize your partition later.

---

