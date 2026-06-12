---
title: "[SOLVED] partitioning and file system definition"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by EdenFuchs on 2008-09-30
trying to install ubuntu8.04.1 in dual boot configuration on a compaq running vista.
1. i have read recommendations in this forum for using the original vista partitioning tool. on the other hand i read that the swap, root, and home partitions should be logical, and there is no place in the vista tool for defining that. I've also read that the root and home directories should best run the Ext3 file system. how do i do that?
thanks!

---

### Post by mikewhatever on 2008-09-30
The only thing to use the Vista tool for is to shrink its partition. Once that's done and you have the unallocated space for Ubuntu, follow this guide->[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall).

That should take care of ext3 and the rest. There is more then one way to set up partitions, however, it doesn't matter if /, /home or swap are logical or not.

---

### Post by Pumalite on 2008-09-30
Check these links:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by EdenFuchs on 2008-09-30
thanks folks,
things may be easier than they appear...

---

