---
title: "memtest falsely reports bad memory"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by heliboy on 2013-03-31
Before attempting to install lubuntu on an IBM Thinkpad 600E with the alternate CD "lubuntu-12.10-alternate-i386", I ran memtest from the CD (after checking the CD itself for errors).  Beginning at 63% completion of a pass, memtest generated endless error reports.  Removed the 128 MB memory stick from the computer, leaving only the 64 MB stick; memtest reported no errors. Bought two new 128 MB sticks and tried all possible combinations of sticks and slot positions; memtest reported innumerable errors whenever a 128 MB stick was present, alone or in combination with another 128 MB stick or the 64 MB stick.  Tried running memtest from the CD "xubuntu-12.04.2-alternate-i386"; memtest found no errors with any configuration of sticks.  Installed xubuntu and ran memtest from the boot menu; memtest found no errors.  Looks like memtest does not run properly under the lubuntu 12.10 alternate installation CD.

---

### Post by Doug S on 2013-03-31
Yes, there was a problem with a memtest version recently.
Sorry, I didn't find a reference yet, I am just going from memory. There was some thread about it on these forums, with version numbers to check for and such, I just didn't find it.

There is also: [http://forum.canardpc.com/threads/72840-Ubuntu-12.10-build-Memtest-v4.20-fails-on-Sandy-Bridge](http://forum.canardpc.com/threads/72840-Ubuntu-12.10-build-Memtest-v4.20-fails-on-Sandy-Bridge)

---

