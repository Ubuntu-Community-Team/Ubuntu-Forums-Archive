---
title: "Skip GRUB on install with 10.04 Alternate Install CD"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by Meson on 2010-07-24
My existing setup:

```

/dev/sda1  boot
/dev/sda2  win7
/dev/sda3  recovery
/dev/sda5  swap
/dev/sda6  <to be: ubuntu (luks)>
/dev/sda7  arch (luks)

```

My boot partition and MBR are already setup, I can boot to win7, recovery, and arch just fine. I will be using the Ubuntu 10.04 Alternate installer. I do not want the alternate installer to disrupt my existing MBR or boot partition.

1) Should I setup /dev/sda1 as /boot during installation? I don't want anything overwritten in there.

2) Where should I tell the installer to install grub? /dev/null?

The only thing I want Ubuntu to be able to use /boot for is to put its kernel image, vmlinuz, and system map (if necessary). It shouldn't be touching /boot/grub.

Thanks!

---

