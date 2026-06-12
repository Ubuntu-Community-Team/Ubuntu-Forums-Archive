---
title: "Crash / boot loop after upgrading from 22.04 to 24.04"
date: 2024-09-25
forum: Installation &amp; Upgrades
---

### Post by TomSoniq on 2024-09-25
Hi!
I'm running an ubuntu server with the following history:
Initially installed 18.04 LTS on it.
No fancy 3rd party drivers, it's just running subversion, nextcloud, some samba shares and FHEM.
Drive is partitioned 512MB VFAT for /boot/efi, 1GB EXT4 for /boot, 15GB EXT4 for /
Upgraded directly and successfully to 22.04.5 just a few days ago (via do-release-upgrade)
Now trying to upgrade to 24.04.1 via do-release-upgrade
The upgrade runs through but when it finally reboots it crashes into a complete unexpected RESET so early that my screen isn't able to show anything.

Things that I've checked already:
Both the desktop and the server live version boot flawlessly on this system.
A fresh server install of 24.04.1 boots flawlessly on this system.
So it can't be a general hardware incompatibility.

Next thing I checked:
On the upgraded installation which constantly crashes I reverted back to binary image backups of my /boot/efi and /boot partitions. This boots perfectly fine into the 24.04.1 root filesystem but of course with the old kernel that came with 22.04.5.
When I then do a simple update-grub, the next boot immediately crashes as before.

There are no fancy grub config options, i.e. I've never edited /etc/default/grub
/etc/grub.d/ contains these:
```
drwxr-xr-x   2 root root  4096 Sep 10 09:23 .
drwxr-xr-x 121 root root 12288 Sep 20 23:07 ..
-rwxr-xr-x   1 root root 10627 Apr 15  2020 00_header
-rwxr-xr-x   1 root root  6260 Dec  2  2022 05_debian_theme
-rwxr-xr-x   1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x   1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x   1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x   1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x   1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x   1 root root   700 Feb 21  2022 35_fwupd
-rwxr-xr-x   1 root root   214 Apr 15  2020 40_custom
-rwxr-xr-x   1 root root   215 Dec 18  2022 41_custom
-rw-r--r--   1 root root   483 Apr 15  2020 README
```

Do you have any hints what I can do to debug this crash and finally find a solution?

Thanks,
Tom

---

