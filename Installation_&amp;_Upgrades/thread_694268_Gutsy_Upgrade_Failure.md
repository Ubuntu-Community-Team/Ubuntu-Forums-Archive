---
title: "Gutsy Upgrade Failure"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by bbarlow on 2008-02-11
I had a working Feisty installed, then I got up at 3 a.m. to upgrade to Gutsy because my satellite ISP has unlimited downloads from 3 a.m. to 6 a.m.  I got it started and went back to bed.  When I got up about 7 a.m., all appeared to be well.  The upgrade manager reported that it had some packages to delete and then asked for a reboot.  It hung on the reboot.  When I hit ESC in Grub and had it boot in recovery mode it stopped with this:

[  33.240244] checking TSC synchronization [CPU#0->CPU#1]:
followed by a blinking cursor.

It would not progress beyond that point.  Also my Feisty live CD won't boot anymore; however, I have an old Knoppix CD that will boot.  When I tried running fsck /dev/hda1 from the Knoppix root terminal, it reported that the file system had unsupported features and that I needed a newer version of the fsck program.

I am pretty much a newbie re: Linux but I have been keeping various MS PCs running for my personal use since about 1985.  I did skip Windows 95 and 98 - I was running OS/2 during that period.

The system has a 3.0 GHz P4 CPU, 1 GB RAM, 160GB HDD, & ASUS MB.

Any help would be greatly appreciated.

---

