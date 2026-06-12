---
title: "Ubuntu 14.04.03 fails to recognize internal eMMC storage"
date: 2018-07-23
forum: Installation &amp; Upgrades
---

### Post by arashesfahany on 2018-07-23
Dear all,

I wanna install Ubuntu 14.04.03 on my UP board which has 32GB of internal eMMC storage. But, both the installer and the live version fail to recognize internal eMMC storage. I also tried Ubuntu 14.04.05 and the problem persists.

With Ubuntu 16.04.03 everything goes fine, but I need to have 14.04.03 for my special purpose.

I also tried to install 14.04 on UP-squared and the exact problem persists.

The UP board's BIOS information is attached.
[ATTACH=CONFIG]280487[/ATTACH]

Does anyone have any idea how to solve this problem?

Tnx

---

### Post by arashesfahany on 2018-07-24
I managed to install 14.04 on a usb flash drive. To my surprise, this installed version, recognizes he internal eMMC!

---

### Post by Autodave on 2018-07-24
You could try what arashesfahany suggested, but I honestly doubt that you are going to have much luck: that old kernel just didn't have support for eMMC.

---

