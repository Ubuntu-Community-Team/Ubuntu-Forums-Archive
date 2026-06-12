---
title: "No grub menu after minimum install"
date: 2016-04-28
forum: Installation &amp; Upgrades
---

### Post by swajime on 2016-04-28
I have installed a minimal 64-bit Ubuntu 14.04 system according to [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) from a PXE-boot.

The install appears to go smoothly, but when rebooting the system there is no grub menu.  Instead I am greeted with the following text:

[INDENT]```
/dev/mmcblk0p1: clean, 60052/656640 files, 342100/2621440 blocks
```[/INDENT]

The computer displays nothing else on the screen, and does not accept any input from the keyboard.

I was able to PXE-boot to rescue mode and install lilo, which works, but I prefer to install grub.

While booted from lilo, I am able to get the following information:

The file /etc/lilo.conf has the following entries:
[INDENT]```
boot = /dev/disk/by-id/mmc-BIWIN_0x000001f6
append = "console=ttyS0,57600 rootfstype=ext4 edd=off"
image = /A/boot/vmlinuz-4.4.0-21-generic
[INDENT]label = "A"
initrd = /A/boot/initrd.img-4.4.0-21-generic[/INDENT]
image = /B/boot/vmlinuz-4.4.0-21-generic
[INDENT]label = "B"
initrd = /B/boot/initrd.img-4.4.0-21-generic[/INDENT]
```[/INDENT]

The file /etc/fstab contains the following:
[INDENT]```
# / was on /dev/mmcblk0p1 during installation
UUID=e98ce3c9-c6ee-4f0a-ba0d-824f3f1482e5 /               ext4    errors=remount-ro 0       1
UUID=e98ce3c9-c6ee-4f0a-ba0d-824f3f1482e5 /A              ext4    errors=remount-ro 0       1
# /alt-root was on /dev/mmcblk0p2 during installation
UUID=4d933c92-fe01-44b4-b444-25570d7842c9 /alt-root       ext4    defaults        0       2
UUID=4d933c92-fe01-44b4-b444-25570d7842c9 /B              ext4    defaults        0       2
# /repo was on /dev/mmcblk0p3 during installation
UUID=ee13c0c3-422a-44ed-acfd-5db9a3681a3b /repo           ext4    defaults        0       2
# swap was on /dev/mmcblk0p4 during installation
UUID=61f561c5-060e-4c04-9fe1-0f1e528ab3e5 none            swap    sw              0       0
```[/INDENT]

The goal here is to have a sytem that can be booted to either /dev/mmcblk0p1 or /dev/mmcblk0p2 from the grub menu.

I am not sure what other information is needed to help fix this, so please let me know what other information to provide.

Any help getting grub to work will be greatly appreciated.

Thanks,


John

---

