---
title: "W8 won't start after Ubuntu install dual boot"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by dupont2 on 2018-04-29
After I installed Ubuntu 18.04 beside W8, W8 does not start until I change the secure mode to UEFI in the Bios.
If I want to boot on Ubuntu, I must change secure mode to legacy in the bios.
How can I select the OS to boot without going in the bios menu each time ?

---

### Post by yancek on 2018-04-29
Your windows 8 is installed in UEFI mode, your Ubuntu is installed in Legacy mode.  What you see is what happens when you do that.  If you want them both to boot from the same menu, you need both either UEFI or both Legacy.  This is all explained at the Ubuntu documentation site below.  It also explains converting Ubuntu to UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

