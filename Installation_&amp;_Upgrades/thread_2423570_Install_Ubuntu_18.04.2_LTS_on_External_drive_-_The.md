---
title: "Install Ubuntu 18.04.2 LTS on External drive - The partition /dev/sda3 assigned to /"
date: 2019-07-25
forum: Installation &amp; Upgrades
---

### Post by akkapolk on 2019-07-25
1. Create a bootable USB stick on Windows (Referece: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)).
2. Boot from the USB stick and select Try Ubuntu.
3. Open GParted and delete all partition on my External drive (Seagate Backup Plus Drive 2 TB).
[IMG]https://docs.google.com/uc?id=1SmR9TWzz8fxz7edpAjbY-zlpvnskL7Uo[/IMG]


4. Install Ubuntu 18.04.2 LTS.
[+] Add swap for 16384 MB (My RAM is 8.00 GB or 8*2*1024 = 16384 MB).
[+] Add efi for 100 MB.
[+] Add ext4 / for the rest.
[IMG]https://docs.google.com/uc?id=1lhHCVWBmWKUTDf5pW6Mh616eEMuIWgWz[/IMG]

5. Click Install Now.
[IMG]https://docs.google.com/uc?id=1Srin8G8ii7Im1u_-BMvOzASFKFhK4wdk[/IMG]

Could you help to suggest me, please?
1. How to fix? ```
The partition /dev/sda3 assigned to / starts at an offset of 2560 bytes from the minimum alignment for this disk, whick may lead to very poor performance.
```
2. What is the correct memory for swap, efi and ext4? All necessary?

---

### Post by oldfred on 2019-07-25
Gparted should have used correct alignment. It has for multiple years. Are you using gpt, not old MBR partitioning?
Post this:
sudo parted -l

New versions of Ubuntu do not need swap partition, it now uses a swap file (like Windows).
I would add ESP as first partition, if lots of space use 300 to 500MB, otherwise 100MB is fine. And often better to have / (root) separate from data. If newer user create / ext4 as 25 or 30GB and rest of drive as /home and/or data partitions. 

Ubuntu's Ubiquity has a long standing bug where it only installs grub to first drive, first NVMe or sda. Initial work around was to copy boot files from ESP on first drive to second drive & use efibootmgr to create correct entry & update fstab with correct UUID for ESP. Now you can correct it during install:
       Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

See link below in my signature for lots of info on UEFI install.

---

### Post by akkapolk on 2019-07-30
> **oldfred said:**
> Gparted should have used correct alignment. It has for multiple years. Are you using gpt, not old MBR partitioning?
Post this:
sudo parted -l

New versions of Ubuntu do not need swap partition, it now uses a swap file (like Windows).
I would add ESP as first partition, if lots of space use 300 to 500MB, otherwise 100MB is fine. And often better to have / (root) separate from data. If newer user create / ext4 as 25 or 30GB and rest of drive as /home and/or data partitions. 

Ubuntu's Ubiquity has a long standing bug where it only installs grub to first drive, first NVMe or sda. Initial work around was to copy boot files from ESP on first drive to second drive & use efibootmgr to create correct entry & update fstab with correct UUID for ESP. Now you can correct it during install:
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

See link below in my signature for lots of info on UEFI install.

Thank you very much.

---

