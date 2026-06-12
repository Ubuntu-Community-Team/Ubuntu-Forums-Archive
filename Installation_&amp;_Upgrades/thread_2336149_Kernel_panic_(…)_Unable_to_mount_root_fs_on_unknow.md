---
title: "Kernel panic (…) Unable to mount root fs on unknown-block(0,0)"
date: 2016-09-05
forum: Installation &amp; Upgrades
---

### Post by justchris123 on 2016-09-05
I have upgraded from Ubuntu 14.04 to 16.04.01 after that there is a problem with grub2 (I have upgraded by sudo apt-get update and sudo do-release-upgrade -d), I am getting an error message: Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0). I have tried as sudo in recovery mode: sudo update-initramfs -u -k $(uname -r) and sudo update grub2 - but it didn't help (I've got an error: Missing /lib/modules/$(uname -r) and could not open directory /lib/modules/$(uname -r)). I got a hint on the other forum that "I noticed "/ was on /dev/sda1 during installation" but your root partition appears to be /dev/sdb1". But I am not a pro, and i would be grateful if someone told me how to ues "mount" in order to fix this.

---

