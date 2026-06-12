---
title: "Install Ubuntu FROM Ubuntu?"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by tester537 on 2010-09-09
Hello,

Can I install Ubuntu from an installation of Ubuntu, rather than using the installation CD?

Specifically, I have Ubuntu 10.04 installed (and bootable) on an SD card, and would like to install from Ubuntu (running on the SD card) to the netbook's hard drive.

Thanks!

---

### Post by oldfred on 2010-09-09
You would have to have the ISO on your SD card and use grub to boot it. You would just have to make sure no install partitions are mounted which should be ok if you are booting the ISO.

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by tester537 on 2010-09-09
Thanks! The directions in the second link fixed it.

---

