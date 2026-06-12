---
title: "Grub error installing 12.10"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by omega552003 on 2012-12-10
I'm having an issue installing Ubuntu 12.10 desktop on an Intel S5520SC system. When it tries to install grub it gets a fatal error that it cant find /dev/sda. If I tell it to select a different destination only /dev/sdb and /dev/sdb1 show up.

This is a fresh install with no EFI set and SATA is set to IDE.

Update: Fixed the issue using this: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) as you can see in the log file i have some raid setup that is interfering with the install. It's odd in the fact the in my BIOS its set to IDE Enhanced.

Grub repair log: [http://paste.ubuntu.com/1424310/](http://paste.ubuntu.com/1424310/)

---

### Post by darkod on 2012-12-10
It would help if you specify where are you installing? Which disk and what partition? Do you have more than one disk (sda and sdb)?

Also, if some disks have traces of raid meta data, installing grub might fail because it will think it's raid and you install on raid differently.

---

### Post by omega552003 on 2012-12-10
> **darkod said:**
> It would help if you specify where are you installing? Which disk and what partition? Do you have more than one disk (sda and sdb)?

Also, if some disks have traces of raid meta data, installing grub might fail because it will think it's raid and you install on raid differently.
I think that is exactly what was happening, the 2 disks are retired 250GB enterprise drives that were on a RAID and i guess one still has the RAID metadata from an LSI controller.

---

### Post by darkod on 2012-12-10
To make sure you delete meta data from both disks, you can do this from live mode:
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb

---

