---
title: "Wont Boot From Flash Drive"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by xkylewrightx on 2010-10-23
Hello everyone.

After many failed attempts, I finally got Ubuntu on my Flash Drive (16gb).
This was completed by downloading Ubuntu Desktop Edition (ubuntu.com), and using The Universal USB Installer to put the .iso on my Flash Drive.

When I try to boot my PC from the flash drive, I get a black screen saying...

"No DEFAULT or UI configuration directive found!
Boot:"

Please help!!!

---

### Post by sikander3786 on 2010-10-23
Rename the isolinux folder on the USB to syslinux. And under syslinux folder two more files isolinux.bin and isolinux.cfg to syslinux.bin and syslinux.cfg respectively. Now it should work.

---

### Post by xkylewrightx on 2010-10-23
I found the isolinux folder in the .iso from Ubuntu.com but it is missing from the flash drive... Should I copy it over manually?

EDIT: I found it. It was already called Syslinux, and the files inside were already named properly.

---

### Post by xkylewrightx on 2010-10-23
In the syslinux folder, there is a isolinux.bin, which i renamed to syslinux.bin. Then there is a isolinux.cfg AS WELL AS a syslinux.cfg. Which .cfg file should be named what? Why is there two?

Thanks!

---

