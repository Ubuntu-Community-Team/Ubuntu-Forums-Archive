---
title: "[ubuntu] failed to sudo update-initramfs -u -k version [sudo] password:  update-initr"
date: 2015-07-12
forum: Installation &amp; Upgrades
---

### Post by zerop2 on 2015-07-12
after compiled kernel and can not boot in vmware
due to error VFS can not mount fs

sudo update-initramfs -u -k 4.2.0
update-initramfs: Generating /boot/initrd.img-4.2.0
grep: /boot/config-4.2.0: No such file or directory
WARNING: missing /lib/modules/4.2.0
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/4.2.0: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_mWhNBH/lib/modules/4.2.0/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_mWhNBH/lib/modules/4.2.0/modules.builtin: No such file or directory

---

### Post by dino99 on 2015-07-12
there are some known issues related to lvm/encryption; is that system having such a config ?

---

### Post by zerop2 on 2015-07-12
[https://drive.google.com/file/d/0B2PgRKgeBo5ZbUpnQ0ZVdExpdkU/view?usp=sharing](https://drive.google.com/file/d/0B2PgRKgeBo5ZbUpnQ0ZVdExpdkU/view?usp=sharing)
i can not find this option in config

---

