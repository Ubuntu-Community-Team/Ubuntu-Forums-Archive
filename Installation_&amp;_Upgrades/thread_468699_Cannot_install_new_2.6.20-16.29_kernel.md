---
title: "Cannot install new 2.6.20-16.29 kernel"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by clamshell on 2007-06-09
After using the update manager and recieving
> E: /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb: failed in buffer_write(fd) (9, ret=-1)
I was pretty much dumb-struck, but after re-trying the update via command line, I got
> The following packages will be upgraded:
  linux-image-2.6.20-16-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.8MB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]?
Preconfiguring packages ...
(Reading database ... 141722 files and directories currently installed.)
Preparing to replace linux-image-2.6.20-16-generic 2.6.20-16.28 (using .../linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb) ...
The directory /lib/modules/2.6.20-16-generic still exists. Continuing as directed.
Done.
Unpacking replacement linux-image-2.6.20-16-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb (--unpack):
 failed in buffer_write(fd) (9, ret=-1): backend dpkg-deb during `./boot/System.map-2.6.20-16-generic': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.20-16-generic
Found kernel: /vmlinuz-2.6.20-15-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

which I suspect means that there is not enough space on /boot for the new kernel (my /boot is only 32 MB).
If this is the case, how can I free some space on /boot (how can I remove one of the older kernels) or at least modfy the partition table (I have GParted installed and enough space after my partitions, but that would mean moving the partitions - they are ext3 - is moving possible)?

My /boot partitions contains:

> abi-2.6.20-15-generic             initrd.img-2.6.20-16-generic
abi-2.6.20-16-generic             lost+found
config-2.6.20-15-generic          memtest86+.bin
config-2.6.20-16-generic          System.map-2.6.20-15-generic
grub                              System.map-2.6.20-16-generic
initrd.img-2.6.20-15-generic      vmlinuz-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak  vmlinuz-2.6.20-16-generic


and /boot/grub contains:

> default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2


Also, my /boot/grub/menu.lst contains:

> title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=1879dcfc-cbab-484f-9f08-6b6d59e3fffe ro quiet splash
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,0)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=1879dcfc-cbab-484f-9f08-6b6d59e3fffe ro single
initrd          /initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=1879dcfc-cbab-484f-9f08-6b6d59e3fffe ro quiet splash
initrd          /initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=1879dcfc-cbab-484f-9f08-6b6d59e3fffe ro single
initrd          /initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


So, please please help. I don't really know what to modify and am scared I might render the system un-bootable. Please excuse me if I have posted this thread in the inapropriate forum.

---

### Post by ART_Adventures on 2007-06-09
My system received the latest update for this kernel too. Each time I boot to this kernel, it displays an error message that says "it failed to StartX", and so I need to boot back to 15 again.

---

