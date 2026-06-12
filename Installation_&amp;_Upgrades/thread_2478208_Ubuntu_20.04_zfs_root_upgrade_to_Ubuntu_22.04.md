---
title: "Ubuntu 20.04 zfs root upgrade to Ubuntu 22.04"
date: 2022-08-19
forum: Installation &amp; Upgrades
---

### Post by agreig-d on 2022-08-19
Hi folks

My software is Ubuntu 20.04 on a zfs root filesystem. sudo do-release-upgrade reports EFI System Partition (ESP) not usable Your EFI System Partition (ESP) is not mounted at /boot/efi. Please ensure that it is properly configured and try again.

The release-upgrade tool doesn't work because it looks for a conventional ext4 type boot partition, whereas zfs root boot is something else.

Is there any workaround, e.g. to upgrade by not using Ubuntu's do-release-upgrade tool?

Many thanks

---

### Post by TheFu on 2022-08-19
You could try the manual Debian method.  Be certain you have excellent backups that can be restored before starting.
In 20.04, ZFS boot support was clearly listed as "experimental". Thanks for experimenting.

---

