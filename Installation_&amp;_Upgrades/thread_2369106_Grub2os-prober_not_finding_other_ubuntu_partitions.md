---
title: "Grub2/os-prober not finding other ubuntu partitions"
date: 2017-08-18
forum: Installation &amp; Upgrades
---

### Post by rick3332 on 2017-08-18
How do I get update-grub to recognize ALL of my ubuntu partitions?

After installing a second Ubuntu Gnome on my new acer aspire switch alpha 12, along side of windows 10, update-grub fails to recognize the first Ubuntu but does see windows and itself. os-prober is missing ubuntu #1, but seems to be looking at the correct partitions. See outputs below.

I tried installing in a similar fashion (minus the windows partition, usng an MBR layout) in virtualbox and it recognizes all ubuntu installs, including them in the grub menu.

I have since disabled uefi/secure boot, deleted all ubuntu parts and used gdisk to convert to MBR, done a startup repair on win10, and once working installed Ubuntu (gnome) once (/boot=ext4 /=btrfs), then again to a second set of partitions. Same issue, os-prober does not find the first install.

I have tried installing a third Ubuntu, /boot and /root are both ext4. Still no go.

I am at a loss. Here is some data:

disk layout:
```
Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x-----------

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1        94498814 273209343 178710530 85.2G  5 Extended
/dev/sda2  *       239616  92397567  92157952   44G  7 HPFS/NTFS/exFAT        win10
/dev/sda3        92399616  94496767   2097152    1G 27 Hidden NTFS WinRE     recovery win 10
/dev/sda5        94498816  95473663    974848  476M 83 Linux                            /boot
/dev/sda6        95475712 173598719  78123008 37.3G 83 Linux                          /  btrfs
/dev/sda7       173600768 174575615    974848  476M 83 Linux                          /boot #2
/dev/sda8       174577664 252700671  78123008 37.3G 83 Linux                        / #2 btrfs
/dev/sda9       252702720 253677567    974848  476M 83 Linux                         /boot #3 only ubuntu  listed/bootable in grub
/dev/sda10      253679616 273209343  19529728  9.3G 83 Linux                       / #3 ext4 only ubuntu  listed/bootable in grub

Partition table entries are not in disk order.
```

output of os-prober:
```
/dev/sda2:Windows 10 (loader):Windows:chain
```

os-prober results from /var/log/syslog:
```
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/mmcblk0p1
Aug 18 13:24:48 Switch-SA5-271 05efi: debug: Not on UEFI platform
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/mmcblk0p1
Aug 18 13:24:48 Switch-SA5-271 10freedos: debug: /dev/mmcblk0p1 is not a FAT partition: exiting
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/mmcblk0p1
Aug 18 13:24:48 Switch-SA5-271 10qnx: debug: /dev/mmcblk0p1 is not a QNX4 partition: exiting
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/mmcblk0p1
Aug 18 13:24:48 Switch-SA5-271 macosx-prober: debug: /dev/mmcblk0p1 is not an HFS+ partition: exiting
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/mmcblk0p1
Aug 18 13:24:48 Switch-SA5-271 20microsoft: debug: /dev/mmcblk0p1 is a FUSE partition
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/mmcblk0p1
Aug 18 13:24:48 Switch-SA5-271 30utility: debug: /dev/mmcblk0p1 is not a FAT partition: exiting
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/mmcblk0p1
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/mmcblk0p1
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/mmcblk0p1
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/mmcblk0p1
Aug 18 13:24:48 Switch-SA5-271 83haiku: debug: /dev/mmcblk0p1 is not a BeFS partition: exiting
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/mmcblk0p1
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/mmcblk0p1
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: /dev/sda1: DOS extended partition; skipping
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Aug 18 13:24:48 Switch-SA5-271 05efi: debug: Not on UEFI platform
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 18 13:24:48 Switch-SA5-271 10freedos: debug: /dev/sda2 is not a FAT partition: exiting
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 18 13:24:48 Switch-SA5-271 10qnx: debug: /dev/sda2 is not a QNX4 partition: exiting
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 18 13:24:48 Switch-SA5-271 macosx-prober: debug: /dev/sda2 is not an HFS+ partition: exiting
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 18 13:24:48 Switch-SA5-271 20microsoft: debug: /dev/sda2 is a NTFS partition
Aug 18 13:24:48 Switch-SA5-271 20microsoft: result: /dev/sda2:Windows 10 (loader):Windows:chain
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 18 13:24:48 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Aug 18 13:24:48 Switch-SA5-271 05efi: debug: Not on UEFI platform
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 18 13:24:48 Switch-SA5-271 10freedos: debug: /dev/sda3 is not a FAT partition: exiting
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 18 13:24:48 Switch-SA5-271 10qnx: debug: /dev/sda3 is not a QNX4 partition: exiting
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 18 13:24:48 Switch-SA5-271 macosx-prober: debug: /dev/sda3 is not an HFS+ partition: exiting
Aug 18 13:24:48 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 18 13:24:48 Switch-SA5-271 20microsoft: debug: /dev/sda3 is a NTFS partition
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Aug 18 13:24:49 Switch-SA5-271 30utility: debug: /dev/sda3 is not a FAT partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Aug 18 13:24:49 Switch-SA5-271 83haiku: debug: /dev/sda3 is not a BeFS partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/efi
Aug 18 13:24:49 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Aug 18 13:24:49 Switch-SA5-271 05efi: debug: Not on UEFI platform
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 18 13:24:49 Switch-SA5-271 10freedos: debug: /dev/sda5 is not a FAT partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 18 13:24:49 Switch-SA5-271 10qnx: debug: /dev/sda5 is not a QNX4 partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 18 13:24:49 Switch-SA5-271 macosx-prober: debug: /dev/sda5 is not an HFS+ partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 18 13:24:49 Switch-SA5-271 20microsoft: debug: /dev/sda5 is not a MS partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Aug 18 13:24:49 Switch-SA5-271 30utility: debug: /dev/sda5 is not a FAT partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Aug 18 13:24:49 Switch-SA5-271 83haiku: debug: /dev/sda5 is not a BeFS partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/efi
Aug 18 13:24:49 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: mounted using GRUB btrfs filesystem driver
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Aug 18 13:24:49 Switch-SA5-271 05efi: debug: Not on UEFI platform
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 18 13:24:49 Switch-SA5-271 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 18 13:24:49 Switch-SA5-271 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 18 13:24:49 Switch-SA5-271 macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 18 13:24:49 Switch-SA5-271 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Aug 18 13:24:49 Switch-SA5-271 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Aug 18 13:24:49 Switch-SA5-271 83haiku: debug: /dev/sda6 is not a BeFS partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/efi
Aug 18 13:24:49 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda7
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Aug 18 13:24:49 Switch-SA5-271 05efi: debug: Not on UEFI platform
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 18 13:24:49 Switch-SA5-271 10freedos: debug: /dev/sda7 is not a FAT partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 18 13:24:49 Switch-SA5-271 10qnx: debug: /dev/sda7 is not a QNX4 partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 18 13:24:49 Switch-SA5-271 macosx-prober: debug: /dev/sda7 is not an HFS+ partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 18 13:24:49 Switch-SA5-271 20microsoft: debug: /dev/sda7 is not a MS partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Aug 18 13:24:49 Switch-SA5-271 30utility: debug: /dev/sda7 is not a FAT partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Aug 18 13:24:49 Switch-SA5-271 83haiku: debug: /dev/sda7 is not a BeFS partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/efi
Aug 18 13:24:49 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda8
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: mounted using GRUB btrfs filesystem driver
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Aug 18 13:24:49 Switch-SA5-271 05efi: debug: Not on UEFI platform
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 18 13:24:49 Switch-SA5-271 10freedos: debug: /dev/sda8 is not a FAT partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 18 13:24:49 Switch-SA5-271 10qnx: debug: /dev/sda8 is not a QNX4 partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 18 13:24:49 Switch-SA5-271 macosx-prober: debug: /dev/sda8 is not an HFS+ partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 18 13:24:49 Switch-SA5-271 20microsoft: debug: /dev/sda8 is not a MS partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Aug 18 13:24:49 Switch-SA5-271 30utility: debug: /dev/sda8 is not a FAT partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Aug 18 13:24:49 Switch-SA5-271 83haiku: debug: /dev/sda8 is not a BeFS partition: exiting
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Aug 18 13:24:49 Switch-SA5-271 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/efi
Aug 18 13:24:50 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/sda9
Aug 18 13:24:50 Switch-SA5-271 05efi: debug: Not on UEFI platform
Aug 18 13:24:50 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda9
Aug 18 13:24:50 Switch-SA5-271 10freedos: debug: /dev/sda9 is not a FAT partition: exiting
Aug 18 13:24:50 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda9
Aug 18 13:24:50 Switch-SA5-271 10qnx: debug: /dev/sda9 is not a QNX4 partition: exiting
Aug 18 13:24:50 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda9
Aug 18 13:24:50 Switch-SA5-271 macosx-prober: debug: /dev/sda9 is not an HFS+ partition: exiting
Aug 18 13:24:50 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda9
Aug 18 13:24:50 Switch-SA5-271 20microsoft: debug: /dev/sda9 is not a MS partition: exiting
Aug 18 13:24:50 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda9
Aug 18 13:24:50 Switch-SA5-271 30utility: debug: /dev/sda9 is not a FAT partition: exiting
Aug 18 13:24:50 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda9
Aug 18 13:24:50 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda9
Aug 18 13:24:50 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda9
Aug 18 13:24:50 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sda9
Aug 18 13:24:50 Switch-SA5-271 83haiku: debug: /dev/sda9 is not a BeFS partition: exiting
Aug 18 13:24:50 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda9
Aug 18 13:24:50 Switch-SA5-271 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda9
```

---

### Post by oldfred on 2017-08-18
Are you loading the btrfs driver in all your installs?
If some are not btrfs then those may not see the btrfs ones unless you add the driver.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

Was Windows UEFI and you converted to BIOS boot? I did not know that was relatively easy to do, I thought it was a full reinstall. And your Product key is in UEFI.

---

### Post by rick3332 on 2017-08-18
> **oldfred said:**
> Are you loading the btrfs driver in all your installs?
If some are not btrfs then those may not see the btrfs ones unless you add the driver.

All are virgin Ubuntu gnome (for the touch screen), all are btrfs ready as they can mount btrfs when booted. All have a /boot that is ext4.

 > **oldfred said:**
> Are you loading the btrfs driver in all your installs?
May be best to see details, you can run from your Ubuntu live installer  or any working install, use ppa version not older Boot-Repair ISO: 

[https://paste.ubuntu.com/25343405/](https://paste.ubuntu.com/25343405/)

> **oldfred said:**
> Are you loading the btrfs driver in all your installs?
Was Windows UEFI and you converted to BIOS boot? I did not know that was  relatively easy to do, I thought it was a full reinstall. And your  Product key is in UEFI.

I thought I would try it. Win10 came installed on this device. I started by making good backups of the device  in a factory pre-first-boot condition, so everything below can be reversed.

First I shrunk windows partition and moved the restore part just after it, leaving at least 1MB at the beginning of each and all free space at the end of the disk. I turned off uefi in the bios, used gparted to  delete all but the main and restore partitions (killed the EFI part), used gdisk to convert back to MBR, ran startup repair  from the acer recovery USB disk I made, and presto!! It booted windows. Havn't tested it in any way other than it boots and seems to work. I havn't given it network access so maybe it would choke when it calls home. 

Then I installed my Ubuntu x2, one as my main install and one to experiment with, and here we are.

---

### Post by oldfred on 2017-08-18
Do not know btrfs and what issues it may add.
Each drive has a separate install of grub. If you boot each of those and run sudo update-grub do you get any error messages or is it just not seeing the other installs at all?

Do not see anything in report that stands out. I do find it easier to not have a separate /boot, but do not know if you can use btrfs as / including /boot or if it must have a separate /boot partition. I have only used ext4 since it is the default with Ubuntu. Fedora was going to make btrfs the standard but just announced it is phasing it out.

I do have multiple UEFI installs on two drives and no issues, but I do not use os-prober. 
Did not use os-prober, with even more installs, on 3 drives with BIOS.
I add my own boot like these in 40_custom to boot by partition, not a specific kernel:
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Just showing first line of some of my installs. A couple are obsolete & I have edited most of those out, but have not updated recently.
```
menuentry "Xenial on sdb3" {
menuentry "Artful 17.10 on sdb9" {
menuentry "Mate 16.10 on sdb10" {
menuentry "trusty 14.04.3 on sdb10" {
menuentry " " {
menuentry 'Live ISOs on SSD' {
menuentry 'Live ISOs on HDD (boot on SSD)' {
menuentry " " {
menuentry "System restart" {
menuentry "System shutdown" {

```

```
menuentry "Artful 17.10 on sdb9" {
    set root=(hd1,gpt9)
        linux /vmlinuz root=/dev/sdb9 ro quiet splash
        initrd /initrd.img
}

```

You would have to add an insmod btrfs and set root to /boot partition and root= to install device.

---

### Post by rick3332 on 2017-08-19
Ok. So os-prober doesn't know how to handle btrfs as Ubuntu sets them  up. Insane. It would be a quick fix for the developers I am sure. Just  look in /@  or maybe /* on btrfs 

Ubuntu installs the root  filesystem in a subvolume called "@" on btrfs. That means grub and os  prober have to use  /mountedbtrfsroot/@/etc/mountedbtrfsroot/@/boot.

The workaround was to create symlinks in the root of the btrfs:
```
cd /mountedbtrfsroot/
ln -s @/boot boot
ln -s @/etc etc

```
Then  update-grub and presto, it finds the installed ubuntu on that partition. An install will always find it's  own files when probed because they are already mounted at /boot and /etc and  update-grub knows to look there.

I hope that heps someone.

Thank you oldfred for making me think to look there again.

---

