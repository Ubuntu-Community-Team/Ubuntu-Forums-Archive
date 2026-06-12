---
title: "drive/partitions not shown"
date: 2012-07-29
forum: Installation &amp; Upgrades
---

### Post by jjbbg on 2012-07-29
I give up---
Been trying for a couple of weeks to install Ubuntu - anything after 9.04.  Here's my setup and problem.
System, quite old, is running Windows XP SP3  on a 250GB hdd and has 2GB ram.  There's a second 250GB hdd that has 3 empty partitions on it that I've reserved for Ubuntu.  I can install versions of Ubuntu up to, and including, 9.04 with no problem.  When I trry to install any later version I can get to the step where I should be able to select the drive/partition but nothing is shown.  Tried running from the live disk and using GParted and then installing but I still get the same thing - no drive or partition to install to.  Have been searching for a solution online and tried just about all suggestions.  Have tried finding something in Ubuntu Forums but gave up after a couple of days.  Also tried many ways of mounting a partition from a terminal but I keep getting the same result - drive does not exist - . Anybody out ther have any suggestions?
Incidentally, have tried installing other Linux distros and have the same problem.
Will certainly appreciate any help.
jjbbg

---

### Post by darkod on 2012-07-29
Hm, it sounds like the disk has been used in raid and has meta data remains. In that case the installer is ignoring it thinking it must belong to a raid array.

Boot into live mode with the ubuntu cd, and in terminal try to remove the meta data. NOTE: do that only if the disk is NOT used in raid right now. If this second disk shows up as /dev/sdb in Gparted for example, the command to remove the meta data would be:
sudo dmraid -E -r /dev/sdb

If it asks you to confirm, do it and you should be fine installing after that.

---

### Post by jjbbg on 2012-07-29
darkod, you are indeed a lifesaver.  Followed your instructions and in less than 5 minutes I was installing Ubuntu 12.04.
Thanks again==
jjbbg

---

