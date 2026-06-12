---
title: "Ubuntu 9.10 not detecting /dev/sdb on install"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by tastech on 2010-04-07
So as the title says, that's the issue. Obviously I can't install to it if I can't select it from the drop down menu. Not that it really matters, but this happens with both 64 and 32 bit versions, clean disc, no errors. I've also tried xubuntu 32-bit.


[LIST]
[*]I can install Slackware on it, or for all I know every other OS.
[*]I can find it with cfdisk, fdisk, gparted, etc.
[*]I can format it in windows and use it as a drive
[*]If I try to install ubuntu from windows on it once I boot into ubuntu to finish the install it goes in an infinite loop of something like 'no root filesystem please reconfigure (or something like that), hit ok, repeates the message until I get tired of hitting ok and reboot.
[*]Always lists it under places as '500gb filesystem' even if there are no assigned partitions on it.
[*]I've rebuilt the partition table with fdisk
[*]analyzed it with disktest (drivetest? something test or testsomething)
[*]I've considered giving up and using another distro...
[/LIST]

Any ideas?

---

### Post by dstew on 2010-04-07
Try this. Boot the Live CD, start Synaptic, and remove completely the package **dmraid**. See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054").

---

