---
title: "Configuring Yaboot to recognize other Linux partitions"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by audiorevolution on 2005-05-22
I have another Linux partition (Debian 'Sarge', hda3) on my drive, and while I configured it so I can mount the partition and read/write to it, I cannot boot into it because Yaboot assumes two options "GNU/Linux" for my Ubuntu 5.04 partition, and "cdrom".  How can I configure Yaboot to allow me to boot into Debian?

---

### Post by audiorevolution on 2005-05-22
My /etc/yaboot.conf file contains the following:

```
# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/hda3.
image=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:3,/boot/vmlinux
    label=hda3-Linux
    root=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:3
    append="root=/dev/hda3 ro"
    initrd=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:3,/boot/initrd.img
```

But no clear way of making this an option to boot from.

---

