---
title: "Configuring 'bootstrap-base' failed during pxe boot"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by peertje86 on 2010-06-21
[LEFT]I'm trying to install ubuntu on an old thin client. It has no cd-drive and does not support usb-boot. therefore I use pxe-boot.
Booting works fine untill installing the base-system. I get a red screen error. Sometimes this happens at 2% and sometimes later. This is what the last part of syslog said.
```

Jun 21 21:16:24 debootstrap: mknod: /target/test-dev-null: Input/output error
Jun 21 21:16:24 kernel: [  574.876077] end_request: I/O error, dev sda, sector 5888
Jun 21 21:16:24 kernel: [  574.876077] ata1: EH complete
Jun 21 21:16:24 kernel: [  574.876077] EXT4-fs error (device sda1): ext4_read_inode_bitmap: Cannot read inode bitmap - block_group = 0, inode_bitmap = 480
Jun 21 21:16:24 kernel: [  574.876077] Aborting journal on device sda1-8.
Jun 21 21:16:24 kernel: [  574.884072] EXT4-fs (sda1): Remounting filesystem read-only
Jun 21 21:16:24 kernel: [  574.888049] EXT4-fs error (device sda1) in ext4_new_inode: IO failure
Jun 21 21:16:24 kernel: [  574.888049] EXT4-fs error (device sda1) in ext4_mknod: IO failure
Jun 21 21:16:24 debootstrap: E: NOEXEC
Jun 21 21:16:24 debootstrap: EF: Cannot install into target '/target' mounted with noexec or nodev
Jun 21 21:17:16 main-menu[248]: (process:11580): mv: cannot rename '/target/etc/fstab.orig': Read-only file system
Jun 21 21:17:16 main-menu[248]: WARNING **: Configuring 'bootstrap-base' failed with error code 1
Jun 21 21:17:16 main-menu[248]: WARNING **: Menu item 'bootstrap-base' failed.
Jun 21 21:17:16 kernel: [  626.950995] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jun 21 21:17:16 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun 21 21:17:16 dhclient: receive_packet failed on eth0: Network is down
Jun 21 21:17:17 dhclient: DHCPOFFER of 192.168.1.11 from 192.168.1.3
Jun 21 21:17:17 dhclient: DHCPREQUEST of 192.168.1.11 on eth0 to 255.255.255.255 port 67
Jun 21 21:17:17 dhclient: DHCPACK of 192.168.1.11 from 192.168.1.3
Jun 21 21:17:17 dhclient: bound to 192.168.1.11 -- renewal in 246 seconds.
Jun 21 21:17:17 main-menu[248]: INFO: Modifying debconf priority limit from 'high' to 'medium'
Jun 21 21:17:17 debconf: Setting debconf/priority to medium
Jun 21 21:17:18 main-menu[248]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Jun 21 21:17:18 main-menu[248]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Jun 21 21:17:18 main-menu[248]: DEBUG: resolver (efi-modules): package doesn't exist (ignored)
Jun 21 21:17:18 main-menu[248]: INFO: Falling back to the package description for console-setup-udeb
Jun 21 21:17:36 main-menu[248]: INFO: Falling back to the package description for console-setup-udeb
Jun 21 21:17:36 main-menu[248]: INFO: Menu item 'di-utils-shell' selected
Jun 21 21:30:11 main-menu[248]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Jun 21 21:30:11 main-menu[248]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Jun 21 21:30:11 main-menu[248]: DEBUG: resolver (efi-modules): package doesn't exist (ignored)
Jun 21 21:30:11 main-menu[248]: INFO: Falling back to the package description for console-setup-udeb
Jun 21 21:30:17 main-menu[248]: INFO: Falling back to the package description for console-setup-udeb
Jun 21 21:30:17 main-menu[248]: INFO: Menu item 'save-logs' selected
Jun 21 21:30:26 dhclient: DHCPREQUEST of 192.168.1.11 on eth0 to 192.168.1.3 port 67
Jun 21 21:30:26 dhclient: DHCPACK of 192.168.1.11 from 192.168.1.3
Jun 21 21:30:26 dhclient: bound to 192.168.1.11 -- renewal in 269 seconds.

```

Can someone tell me what is going wrong?
[/LEFT]

---

