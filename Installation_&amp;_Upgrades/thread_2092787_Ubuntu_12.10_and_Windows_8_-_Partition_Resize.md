---
title: "Ubuntu 12.10 and Windows 8 - Partition Resize"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by DarthScape on 2012-12-08
I installed Windows 8, taking up the full 128gb SSD first, single partition and volume called System Reserved. I then proceeded to install Ubuntu 12.10, and gave it about 20gb, while shrinking the Windows side, no swap. It booted into Ubuntu fine. I have since gone back and forth between the two. The problem is that when I boot to Windows, the C: drive shows that it is taking the full SSD, not shrunken at all. I think this may be a problem in the future, as it may write over Ubuntu. Has anyone else seen this? I tried searching, but maybe not hard enough.

---

### Post by oldfred on 2012-12-09
Post this:

       sudo parted /dev/sda unit s print

    
Windows also keeps the same partition info inside the NTFS partition boot sector. If Windows did not run chkdsk on the resize then you may need to run chkdsk or Windows my try writing into the sectors that are really Linux.

---

### Post by DarthScape on 2012-12-09
Just before you posted this, Windows gave me a prompt about a problem with the disk and suggested I restart. I believe that it did a check upon reboot, and now it shows the correct number. Thanks for the solution still!

---

