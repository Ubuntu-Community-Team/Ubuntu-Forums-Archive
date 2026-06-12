---
title: "Dualboot Ubuntu 18.04 and Leap 15 on XPS13"
date: 2018-12-16
forum: Installation &amp; Upgrades
---

### Post by terjejh on 2018-12-16
My XPS13 (9370) had Ubuntu 16.04 factory preinstalled from Dell. I add-installed Leap15 and a dualboot selection menu for Leap15 and Ubuntu was created. Later I upgraded 16.04 to 18.04, when it became available.

The issue is that the dualboot menu disappear after each Ubuntu upgrade, and the machine boots directly to Ubuntu. To fix this, I have used to boot Leap15 from its usb install media and reinstalled the bootloader, which re-creates the dualboot menu.

To avoid this extra step, is there a way to tell Ubuntu that Leap15 coexist on the machine, so that the dualboot menu is kept intact during upgrade (I am relative novice with Ubuntu)?

The XPS13 SSD is partitioned with File systems as follows:

p1 EFI
p2 FAT Win Data OS
p3 Ext4 Ubuntu
p4 Swap
p5 Ext4 Leap
p6 Ext4 (free)


Thanks,
Terje

---

