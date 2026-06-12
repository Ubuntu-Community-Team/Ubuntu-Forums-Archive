---
title: "gParted wont allow hfs+ partition"
date: 2014-11-27
forum: Installation &amp; Upgrades
---

### Post by UncleRoy on 2014-11-27
Back again. Using an imac. Ultimately wish OSX / Ubuntu dual boot under rEFInd .Need to partition ... Boot to usb 14.10 boot stick. Now with AppleMagicMouse working. I find and use gParted but cannot create hfs+ partition (needed for rEFInd install). In gparted hfs+ option is visible but not available. Why is it so? Can anyone help.

---

### Post by coffeecat on 2014-11-27
You need the packages hfsutils and hfsprogs. In gparted, View -> File System Support tells you which packages are needed for which filesystems. If you are booting from a live USB, those packages will be lost when you power down. Is it possible to use the MacOS Disk Utility to create the hfs+ partition?

---

