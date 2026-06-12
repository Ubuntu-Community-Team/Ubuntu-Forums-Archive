---
title: "unable to boot to sdb1 after installing ubuntu-13.10-server-amd64 from USB stick"
date: 2013-12-06
forum: Installation &amp; Upgrades
---

### Post by lindevox on 2013-12-06
Hi 
I've created ubuntu-13.10-server-amd64 with Universal-USB-Installer-1.9.5.1.exe with windows7
After using the USB stick to install on my PC ( Gigabyte GA-H77N-WIFI ), it just won't boot from my hdd.
it will boot from USB stick but not rom hdd (sdb1)
any help?

---

### Post by ubfan1 on 2013-12-06
Sometimes the grub installer gets the disks named/numbered wrong (bug #384633), particularly when not installing to hda (first hard disk). When your install target is after the live media, the use of an actual device like /dev/sdc, will be wrong after the live media is removed, and the target is now sdb.  You can edit the grub commands, changing the names of the disks to be one letter less, ( just on the linux kernel line after "root=/dev/sdx" .  I tend to also reduce the hd2... references to hd1 and the boot works.  Immediately run sudo update_grub to fix the problems (by using UUIDs instead of devices which do not change).

---

