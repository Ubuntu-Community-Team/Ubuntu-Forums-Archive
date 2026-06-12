---
title: "Am I in for a long wait ?"
date: 2024-06-07
forum: Installation &amp; Upgrades
---

### Post by grey1beard on 2024-06-07
I'm in the process of upgrading from 18.04 to 22.04, via 20.04 on an hp laptop, following online instructions at [https://medium.com/@BabajideKale/upgrading-from-ubuntu-18-04-lts-to-22-04-lts-adf5f4a54ffa]("https://medium.com/@BabajideKale/upgrading-from-ubuntu-18-04-lts-to-22-04-lts-adf5f4a54ffa")

```
sudo apt install update-manager-core
sudo do-release-upgrade
``` was the last instruction entered, and Terminal then told me to re-boot.
This I did, but everything froze, and I couldn't restart, nor even turn off the laptop.

Subsequently, I powered off using the on/off switch, and then powered up, but the process has stopped at the splash screen.
Do I now have a long, patient wait, or has something else gone wrong ? :(

---

### Post by yancek on 2024-06-07
At least part of your problem is that you waited too long to upgrade 18.04.  Support for 18.04 ended more than a YEAR ago so that updating and upgrading from the repositories won't work because they are not on the server they were on when it was supported.  I expect the instructions on that site would have worked had you done it on or before April, 2023.  Now download 22.04 (if that is your choice) and put the installer on a USB and install it then copy your personal data to a partition you create on the drive, be it a separate /home partition or a /data partition.l

---

### Post by grey1beard on 2024-06-07
Thanks yancek.
I suspected that would have to be my way forward, so off I go !
Regards, John

---

