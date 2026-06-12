---
title: "Grub update"
date: 2019-11-27
forum: Installation &amp; Upgrades
---

### Post by P-I H on 2019-11-27
Today's update of Grub in Ubuntu 19.10 also updated BIOS on my motherboard MSI Tomahawk B350. The boot disk was changed from /dev/nvme0n1 to /dev/sda. Took some time before I understood what happened, but everything is OK again after a change in BIOS.
```
Start-Date: 2019-11-27  21:19:33
Commandline: aptdaemon role='role-commit-packages' sender=':1.776'
Upgrade: grub-common:amd64 (2.04-1ubuntu12, 2.04-1ubuntu12.1), grub2-common:amd64 (2.04-1ubuntu12, 2.04-1ubuntu12.1), grub-pc:amd64 (2.04-1ubuntu12, 2.04-1ubuntu12.1), grub-pc-bin:amd64 (2.04-1ubuntu12, 2.04-1ubuntu12.1), grub-efi-amd64-bin:amd64 (2.04-1ubuntu12, 2.04-1ubuntu12.1), grub-efi-amd64-signed:amd64 (1.128+2.04-1ubuntu12, 1.128.1+2.04-1ubuntu12.1), libnss3:amd64 (2:3.45-1ubuntu2, 2:3.45-1ubuntu2.1)
End-Date: 2019-11-27  21:20:12

```

---

### Post by oldfred on 2019-11-27
Grub may update UEFI or BIOS boot entry on drive.

UEFI or BIOS install?
If you ever installed in BIOS mode to sda, then grub saves a drive, by device name as place to update.

---

