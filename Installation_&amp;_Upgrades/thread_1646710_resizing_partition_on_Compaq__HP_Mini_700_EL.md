---
title: "resizing partition on Compaq / HP Mini 700 EL"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by bigblackcar on 2010-12-16
Hi everyone,
 I'm trying to install Ubuntu on my Mini 700 EL and when I start it doesn't give me the option to install it alongside Windows.
Wubi does not give me the option to install onto the system, only to reboot and install it completely.
When I try to install from booting from the USB key, I decide to edit partitions manually and I don't get the option of resizing the Windows partition, I can only delete it.

But I need to keep Windows on the machine, unfortunately.
Any suggestion?

---

### Post by Quackers on 2010-12-16
Boot into Windows and go to the disk management console.
First check that you don't already have 4 primary partitions! If you do you will need to delete one before creating any more.
If you have 3 or less primarys you will likely need to shrink one of them to create some free space for Ubuntu to install into.
Right-click the partition you want to resize and select "shrink" then follow the directions.
NB.  It is recommended to defrag the system at least once and preferrably twice, before shrinking Windows partitions!

---

### Post by bigblackcar on 2011-01-10
Thanks. In the end, I downloaded a partition manager and changing the size of the Windows main partition (after a Defrag) worked fine.

---

