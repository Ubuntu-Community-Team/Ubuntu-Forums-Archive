---
title: "Ubuntu - no grub menu and cannot find root.disk"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by 06wjwensley on 2010-11-12
Hi guys - I've got a desktop machine I'm using at home which has vista business installed. I decided to move to ubuntu because vista is so dismally slow and so I downloaded the .iso file, mounted it and installed it from inside windows as a dual boot. Install goes fine, it restarts and I select Ubuntu from the boot menu and then from the grub menu - but it gives me the error message ALERT! /ubuntu/disks/root.disk does not exist! Dropping to a shell... And it refuses to boot. I uninstalled and reinstalled three times but the same error came up. So I pressed e at the grub menu to configure boot options and it seemed like it was trying to boot off my slave drive, which had no ubuntu partition on it. So I changed it from "hdd1, msdos1" to "hdd0, msdos0" and it booted fine. Then this morning when I went to turn it on, there was not even a grub menu, and apparently there was no root.disk either - it just dumped me straight onto grub command line -.- I've checked my ubuntu folder and sure enough root.disk is in there, in all it's 30gb glory - please help!

---

### Post by sikander3786 on 2010-11-12
Instead of installing inside Windows, I would recommend to install it in a true dual-boot with Windows.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Wubi is just intended for testing. It is slower, problematic and whatever.

If you want to use Ubuntu as a production OS, I'll not recommend Wubi if you dare to dual boot.

---

### Post by bcbc on 2010-11-12
FYI, to extract data from a root.disk you can use a program called [ext2read]("http://ext2read.blogspot.com/").

I'm not sure what might be causing your problems. It sounds like your bios is flipping the drive ordering.

If you don't mind playing around, you can probably boot the disk manually from the grub prompt. But it doesn't sound like a good long term solution. [http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

