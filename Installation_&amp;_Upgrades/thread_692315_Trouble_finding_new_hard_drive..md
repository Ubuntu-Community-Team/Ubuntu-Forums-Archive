---
title: "Trouble finding new hard drive."
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by kjd781 on 2008-02-09
Installing Ubuntu 7.10 64x

BIOS reports drive as:

Primary IDE: WD1600  8455 MB
Cyl 16383
Head 16
Sector 63

Live CD runs perfect. When trying to install to HD installation stops at 50%. Gparted "Scan for Devices" reports " No Devices Found"

sudo lshw -C disk reports CD drive only
sudo fdisk -l reports CD drive only.

Not sure what happened to IDE HDD

Any suggestions would be gratefully appreciated.

---

### Post by pieisgood4589 on 2008-02-09
I took out the HD, booted up the computer for 5 seconds just to let it know that it's not there, turned it off, and popped in the HD. Then the install went great!

---

### Post by kjd781 on 2008-02-09
Thanks for your quick response. Just ran through your suggestion but still get the same response. The drive is recognized in the BIOS but does not show up anywhere else.

If you thinkk of anything else i will be grateful

---

