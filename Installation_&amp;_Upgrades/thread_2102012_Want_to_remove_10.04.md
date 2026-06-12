---
title: "Want to remove 10.04"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by vkadal on 2013-01-06
By some mistake I   have 2 installation in my desktop, Ubuntu 10.04 and 12.04. I want to remove 10.04 from my system. Kindly advice me for removal

---

### Post by dino99 on 2013-01-06
all depend on how your installations have been made:
 is there a separate /home partition (not a home folder) to get your data safe ?

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

if your data is safe, then format the 10.04 partition, and reinstall grub:

sudo grub-install /dev/sda
sudo update-grub

note: if each installation have its own swap partition, then format also the 10.04's swap one.

---

