---
title: "How to install xp on a system that already has ubuntu (and still keep ubuntu)"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by MrHuaRen on 2010-10-23
I want to duel boot XP and ubuntu, but have been using ubuntu for quite some time. I want to add a windows section to my computer - but how do I do this with out erasing ubuntu?

---

### Post by oldfred on 2010-10-23
How are your partitions used and do you have space for XP. You need a primary partition formated as NTFS to install XP.

[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)
A Windows partition should be at least 20 Gb (recommended 30 Gb for Vista/Windows 7)

Older but goes over some of the issues, but use grub2 not any of the other alternatives shown:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

You will have to reinstall grub2 as windows will put its bootloader in the MBR. Make sure you have a current liveCD to reinstall grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by john77eipe on 2010-10-24
What about virtual box?

---

