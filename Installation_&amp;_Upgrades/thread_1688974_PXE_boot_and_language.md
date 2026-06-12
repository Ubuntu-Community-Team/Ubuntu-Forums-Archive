---
title: "PXE boot and language"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by gnumdk on 2011-02-16
Since Maverick, i can't set language at boot time via pxe boot.

Here my conf:
LABEL Ubuntu
        menu label Ubuntu
        kernel  ubuntu/casper/vmlinuz
        append boot=casper netboot=nfs nfsroot=194.254.*.4:/home/tftpboot/ubuntu quiet splash initrd=ubuntu/casper/initrd.lz – debian-installer/language=fr console-setup/layoutcode?=fr consolesetup/variantcode?=oss

debian-installer/language=fr seems to be ignored by Ubuntu live. It was working with previous Ubuntu versions.

---

