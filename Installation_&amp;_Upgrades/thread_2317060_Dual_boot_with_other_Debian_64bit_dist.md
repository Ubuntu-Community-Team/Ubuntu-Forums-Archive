---
title: "Dual boot with other Debian 64bit dist"
date: 2016-03-13
forum: Installation &amp; Upgrades
---

### Post by hezy2 on 2016-03-13
Hi,
How can I install a 64bit Debian system alongside with Ubuntu 15.10-x64? The DH is 500GB- one partition, with Ubuntu on it. Thx,
Hezy.

---

### Post by fantab on 2016-03-13
You will have to create a seperate partition for the new OS to install.

---

### Post by Bucky Ball on 2016-03-13
Or just leave free space and use the 'Something Else' option at the partitioning section, if Debian has one.

---

### Post by oldfred on 2016-03-13
Also you need to keep track of which system's grub is booting. Generally last installed is in MBR if BIOS. If UEFI you may have both entries.

Also better to create /mnt/data or /media/$USER/data for any data you want in both systems.
I install multiple copies of Ubuntu and just create another / (root) of about 25GB. Since all data is in data partition(s), / does not have to be large.

During install you may have option on where to install grub2's boot loader. (if BIOS)
Or you can boot back into Ubuntu and reinstall its grub2 boot loader to MBR.

After install run this:
 Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 



Best to know where each system is installed and details. I run Summary Repair and save a copy as part of backup, so I have details of installs.

---

