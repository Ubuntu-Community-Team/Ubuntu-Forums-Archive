---
title: "Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-qu"
date: 2019-06-08
forum: Installation &amp; Upgrades
---

### Post by sspree77 on 2019-06-08
I'm on Ubuntu 19.04 live USB drive. Using "Disk Utility" I'm trying to format a disk partition (/dev/sda7) and I get this error: > Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)

  Background: I had Ubuntu 16.04 installed in /dev/sda7. I was trying to install Ubuntu 19.04 from a live USB stick. During the installation I gave the same /dev/sda7 to use as /. The installation was stuck at creating ext4 partition for about 1 hr and at this point I restarted the system.
  Using gparted UI just shows my entire hard-disk with exclamation mark. It don't show any partitions in UI

---

### Post by Xian on 2019-06-09
There's been numerous reports of this error .... you might want to review this bug:

[https://bugs.launchpad.net/debian/+source/util-linux/+bug/1059872](https://bugs.launchpad.net/debian/+source/util-linux/+bug/1059872)

---

