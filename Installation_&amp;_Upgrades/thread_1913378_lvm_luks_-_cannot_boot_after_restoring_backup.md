---
title: "lvm luks - cannot boot after restoring backup"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by vangop on 2012-01-22
i have restored my system backup like i always did. restored onto luks encrypted lvm.
lnstalled grub, recreated initrd
but the boot fails with ALERT  /dev/mapper/vg1-root doesnt exist
i can see dmcrypt module is not loaded. also during update-initramfs dmcrypt hook was executed after lvm. looks like it 1st tries to load lvm but should crypt instead!
any ideas?
typed from phone

---

### Post by vangop on 2012-01-24
had to reinstall the system. have no clue why this didn't work.

---

