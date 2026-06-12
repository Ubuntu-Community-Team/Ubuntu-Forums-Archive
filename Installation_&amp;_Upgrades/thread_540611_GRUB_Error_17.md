---
title: "GRUB Error 17"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by xterra386 on 2007-09-01
I had installed Ubuntu 7.04 on my Toshiba Satellite X10 laptop and ran for a few days but noticed that it had some issues. I took out my recovery CD for the Toshiba and began to delete the main partitions where Ubuntu was installed and recovered the original OS and Apps for the laptop. 

Everything goes fine and I have 1 NTFS partition like it was before Ubuntu but now I get this upon boot-up


GRUB Loading stage1.5


GRUB loading, please wait...
Error 17


Any ideas on how to fix this problem?

---

### Post by Pumalite on 2007-09-01
Delete

---

### Post by merlinus on 2007-09-01
You will need to restore the windows bootloader to the mbr.

Boot with your recovery cd and look for an option called fixmbr, or you can use supergrub to do this:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

