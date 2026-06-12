---
title: "Linux Image 3.2.0-24 Generic (USB Flash)"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by aaazman on 2012-05-26
Folks:

How do you get to install this on a USB flash drive? I tried to install it in the following manner, but this linux image is always the culprit.

1. I installed Ubuntu 12.04 onto a 16GB flash drive.

2. After booting another 4GB Mint pre-installed flash drive, I re=inserted the 16GB. Invoked GParted and deleted the casper-rw file, reduce the remaining partition size, and created a new EXT4 partition (named casper-rw) to about 14.7 GB onto the 16 GB flash drive.

3. Reboot with the 16GB with Ubuntu 12.04 and invoked the Update Manager and proceeded with Check and Install.

At this point to the upgrade attempt, Ubuntu always generate the following error:

Errors were encountered while processing:
 linux-image-3.2.0-24-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


I can't uninstall this image. At every upgrade attempt, it will generate these errors!

What gives?

---

