---
title: "Update froze computer"
date: 2024-07-10
forum: Installation &amp; Upgrades
---

### Post by oygle on 2024-07-10
Operating System: Kubuntu 23.10
KDE Plasma Version: 5.27.8
KDE Frameworks Version: 5.110.0
Qt Version: 5.15.10
Kernel Version: 6.5.0-42-generic (64-bit)
Graphics Platform: X11
Processors: 4 × Intel® Core&#8482; i5-7300U CPU @ 2.60GHz
Memory: 7.6 GiB of RAM
Graphics Processor: Mesa Intel® HD Graphics 620
Manufacturer: LENOVO
System Version: ThinkPad T470s

Have never had this happen before with a ** sudo apt update**, but today it totally froze the computer. Had to do a power down and reboot. Logs ..

> 
Log started: 2024-07-11  09:01:27
Selecting previously unselected package linux-modules-6.5.0-44-generic.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 244629 files and directories currently installed.)
Preparing to unpack .../0-linux-modules-6.5.0-44-generic_6.5.0-44.44_amd64.deb ...
Unpacking linux-modules-6.5.0-44-generic (6.5.0-44.44) ...
Selecting previously unselected package linux-image-6.5.0-44-generic.
Preparing to unpack .../1-linux-image-6.5.0-44-generic_6.5.0-44.44_amd64.deb ...
Unpacking linux-image-6.5.0-44-generic (6.5.0-44.44) ...
Selecting previously unselected package linux-modules-extra-6.5.0-44-generic.
Preparing to unpack .../2-linux-modules-extra-6.5.0-44-generic_6.5.0-44.44_amd64.deb ...
Unpacking linux-modules-extra-6.5.0-44-generic (6.5.0-44.44) ...
Preparing to unpack .../3-linux-generic_6.5.0.44.44_amd64.deb ...
Unpacking linux-generic (6.5.0.44.44) over (6.5.0.42.42) ...
Preparing to unpack .../4-linux-image-generic_6.5.0.44.44_amd64.deb ...
Unpacking linux-image-generic (6.5.0.44.44) over (6.5.0.42.42) ...
Selecting previously unselected package linux-headers-6.5.0-44.
Preparing to unpack .../5-linux-headers-6.5.0-44_6.5.0-44.44_all.deb ...
Unpacking linux-headers-6.5.0-44 (6.5.0-44.44) ...


The previous update (yesterday) had no errors ..

> 
Log started: 2024-07-10  09:50:25
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 244629 files and directories currently installed.)
Preparing to unpack .../0-grub2-common_2.12~rc1-10ubuntu4.2_amd64.deb ...
Unpacking grub2-common (2.12~rc1-10ubuntu4.2) over (2.12~rc1-10ubuntu4) ...
Preparing to unpack .../1-grub-pc_2.12~rc1-10ubuntu4.2_amd64.deb ...
Unpacking grub-pc (2.12~rc1-10ubuntu4.2) over (2.12~rc1-10ubuntu4) ...
Preparing to unpack .../2-grub-pc-bin_2.12~rc1-10ubuntu4.2_amd64.deb ...
Unpacking grub-pc-bin (2.12~rc1-10ubuntu4.2) over (2.12~rc1-10ubuntu4) ...
Preparing to unpack .../3-grub-common_2.12~rc1-10ubuntu4.2_amd64.deb ...
Unpacking grub-common (2.12~rc1-10ubuntu4.2) over (2.12~rc1-10ubuntu4) ...
Preparing to unpack .../4-grub-efi-amd64-signed_1.197.2+2.12~rc1-10ubuntu4.2_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.197.2+2.12~rc1-10ubuntu4.2) over (1.197+2.12~rc1-10ubuntu4) ...
Preparing to unpack .../5-grub-efi-amd64-bin_2.12~rc1-10ubuntu4.2_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.12~rc1-10ubuntu4.2) over (2.12~rc1-10ubuntu4) ...
Setting up grub-common (2.12~rc1-10ubuntu4.2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up grub-efi-amd64-bin (2.12~rc1-10ubuntu4.2) ...
Setting up grub2-common (2.12~rc1-10ubuntu4.2) ...
Setting up grub-pc-bin (2.12~rc1-10ubuntu4.2) ...
Setting up grub-pc (2.12~rc1-10ubuntu4.2) ...
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-42-generic
Found initrd image: /boot/initrd.img-6.5.0-42-generic
Found linux image: /boot/vmlinuz-6.5.0-41-generic
Found initrd image: /boot/initrd.img-6.5.0-41-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
Setting up grub-efi-amd64-signed (1.197.2+2.12~rc1-10ubuntu4.2) ...
Trying to migrate /boot/efi into esp config
Installing grub to /boot/efi.
Installing for x86_64-efi platform.
Installation finished. No error reported.
Processing triggers for install-info (7.0.3-2) ...
Processing triggers for man-db (2.11.2-3) ...
Log ended: 2024-07-10  09:50:40


I have no idea if there has been any damage to the data (SSD).

---

### Post by oygle on 2024-07-10
Did a full backup, then ..

```
sudo apt upgrade
```

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```
sudo dpkg --configure -a
```

> Setting up linux-modules-6.5.0-44-generic (6.5.0-44.44) ...
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 6.5.0.44.44); however:
  Version of linux-headers-generic on system is 6.5.0.42.42.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-6.5.0-44-generic (6.5.0-44.44) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-6.5.0-42-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-6.5.0-42-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-6.5.0-44-generic
I: /boot/initrd.img is now a symlink to initrd.img-6.5.0-44-generic
Setting up linux-modules-extra-6.5.0-44-generic (6.5.0-44.44) ...
Setting up linux-image-generic (6.5.0.44.44) ...
Processing triggers for linux-image-6.5.0-44-generic (6.5.0-44.44) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-6.5.0-44-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-44-generic
Found initrd image: /boot/initrd.img-6.5.0-44-generic
Found linux image: /boot/vmlinuz-6.5.0-42-generic
Found initrd image: /boot/initrd.img-6.5.0-42-generic
Found linux image: /boot/vmlinuz-6.5.0-41-generic
Found initrd image: /boot/initrd.img-6.5.0-41-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
Errors were encountered while processing:
 linux-generic


---

### Post by oygle on 2024-07-16
It seems okay now, so I guess it is 'solved'

---

