---
title: "Raid1 Installation"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by ptmuldoon on 2012-05-05
Can you install Ubuntu onto a Raid1 software (mdadm) configuration?   I think you can, but you should use/need the alternative CD to do so?

---

### Post by darkod on 2012-05-05
Yes, and yes.

There is an option to do it from the liveCD, but additional preparation steps need to be taken. You will need to install the mdadm package in live mode and make the array. Then start the installation and install onto the array.

Personally, I find the alternate installer much better for mdadm.

---

