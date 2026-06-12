---
title: "Attempt to mount a file system with type vfat in /dev/nvme0n1p1 at /boot/efi failed"
date: 2021-12-21
forum: Installation &amp; Upgrades
---

### Post by gakman on 2021-12-21
Hi,

I've been trying to install Ubuntu 21.10 with various partitioning options and BIOS options, always ending up with the same error after many attempts with different options.

> 
The attempt to mount a file system with type vfat in /dev/nvme0n1p1 at /boot/efi failed.

You may resume partitioning from the partitioning menu.


Logs show:

> 
Dec 21 22:40:52 ubuntu ubiquity[1855]: debconffilter_done: ubi-partman (current: ubi-partman)
Dec 21 22:40:52 ubuntu ubiquity[1855]: Step_before = stepPartAsk
Dec 21 22:40:52 ubuntu kernel: Lockdown: archdetect: /dev/mem,kmem,port is restricted; see man kernel_lockdown.7
Dec 21 22:40:52 ubuntu kernel: Lockdown: archdetect: /dev/mem,kmem,port is restricted; see man kernel_lockdown.7
Dec 21 22:40:52 ubuntu clock-setup[8409]: rdate called using NTP server ntp.ubuntu.com.
Dec 21 22:40:53 ubuntu kernel:  nvme0n1: p1 p2
Dec 21 22:40:53 ubuntu kernel: Lockdown: archdetect: /dev/mem,kmem,port is restricted; see man kernel_lockdown.7
Dec 21 22:40:53 ubuntu kernel: Lockdown: archdetect: /dev/mem,kmem,port is restricted; see man kernel_lockdown.7
Dec 21 22:40:53 ubuntu partman[8942]: mke2fs 1.46.3 (27-Jul-2021)
Dec 21 22:41:01 ubuntu systemd-resolved[1446]: Clock change detected. Flushing caches.
Dec 21 22:41:01 ubuntu clock-setup[8945]: Tue Dec 21 22:41:01 UTC 2021
Dec 21 22:41:01 ubuntu clock-setup[8946]: rdate: adjust local clock by 0.038508 seconds
Dec 21 22:41:01 ubuntu kernel: Lockdown: archdetect: /dev/mem,kmem,port is restricted; see man kernel_lockdown.7
Dec 21 22:41:01 ubuntu ubiquity[8393]: mount: /target/boot/efi: wrong fs type, bad option, bad superblock on /dev/nvme0n1p1, missing codepage or helper program, or other error.
Dec 21 22:41:01 ubuntu kernel: EXT4-fs (nvme0n1p2): mounted filesystem with ordered data mode. Opts: errors=remount-ro. Quota mode: none.
Dec 21 22:41:01 ubuntu kernel: FAT-fs (nvme0n1p1): bogus number of reserved sectors
Dec 21 22:41:01 ubuntu kernel: FAT-fs (nvme0n1p1): Can't find a valid FAT filesystem
Dec 21 22:41:02 ubuntu ubiquity[1855]: switched to page timezone


lsblk:

> 
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0         7:0    0   2.3G  1 loop /rofs
loop1         7:1    0     4K  1 loop /snap/bare/5
loop2         7:2    0  99.3M  1 loop /snap/core/11743
loop3         7:3    0  61.8M  1 loop /snap/core20/1169
loop4         7:4    0  65.2M  1 loop /snap/gtk-common-themes/1519
loop5         7:5    0 150.4M  1 loop /snap/firefox/631
loop6         7:6    0  54.2M  1 loop /snap/snap-store/557
loop7         7:7    0 242.3M  1 loop /snap/gnome-3-38-2004/76
sda           8:0    0 931.5G  0 disk
&#9492;&#9472;sda1        8:1    0 931.5G  0 part /cdrom
nvme0n1     259:0    0 476.9G  0 disk
&#9500;&#9472;nvme0n1p1 259:1    0   512M  0 part
&#9492;&#9472;nvme0n1p2 259:2    0 476.4G  0 part /target


The laptop is a Razer Blade 15, and had Windows 10 on it. I've nuked the partitions and going full disk Ubuntu.

In the BIOS fast boot is off and secure boot is on, although (I think) I tried secure boot off a few times too. I also tried enabling and not enabling secure boot via the install (when choosing third party drivers).

I've tried booting two different ways, a USB disk and MicroSD (via USB adapter).

Not sure how else to debug this, after a lot of searching. Please let me know what I can do help work out this issue.

Thanks!

---

### Post by gakman on 2021-12-21
I went the nuclear option and dd zero's onto the first MB of the disk. Worked first go after a reboot.

---

