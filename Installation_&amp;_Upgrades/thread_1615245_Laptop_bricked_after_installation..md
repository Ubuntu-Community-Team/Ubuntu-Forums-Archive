---
title: "Laptop bricked after installation."
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by gnrak on 2010-11-06
Laptop Specs: 
HP Pavillion DV6500 
AMD Turion 64 
Vista 64
Ubuntu 8 on ext3 partition (before install)  

Used Unetbootin on Windows to create USB installer for Ubuntu 10.10 Desktop 32 bit.  

Installed successfully on a desktop (also amd64) a week ago. 

Tried installing it on laptop today with same USB drive.  Installation was a bit slow between screens up to and including HDD partitioning. Freed old Ubuntu partition and created ext4 and swap partitions. Normal speed after that.  

Other than that, installed with seemingly no issues.  Took out USB stick when prompted and pressed enter. Laptop rebooted to a black screen with LED activity indicators idle. No BIOS activity at all.  

Would the installation really corrupt the BIOS? Did I do something wrong? Any help would be greatly appreciated.

---

### Post by spcwingo on 2010-11-06
Directly after POST frantically press shift.  At the grub menu on your first Ubuntu entry press "e" to edit.  At the end of the kernel line enter:

```
xforcevesa
```

---

