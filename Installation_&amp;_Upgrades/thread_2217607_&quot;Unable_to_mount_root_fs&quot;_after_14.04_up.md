---
title: "&quot;Unable to mount root fs&quot; after 14.04 upgrade of Full Disk Encryption install"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by nx1101 on 2014-04-18
Here's the error I got immediately after an otherwise seamless upgrade from 13.10:

VFS: Cannot open root device "mapper/host-root" or unknown-block(0,0): error -6
Please append a correct "root=" boot option; here are the available partitions: (blank)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

This is on a full disk encrytpion disk. grub.conf appears sane. Booting into a live CD I can still mount the encrypted disk and o can confirm the initrd images are present. However it does appear to be the old kernel. Any tips on how to proceed?

Thanks

---

### Post by nx1101 on 2014-04-18
I was able to fix the issue by taking the following steps.

1. Boot into 14.04 Live CD
2. [Chroot]("http://ubuntuforums.org/showthread.php?t=1156240") to disk with broken Ubuntu install
3. # update-initramfs -d -k all
4. # apt-get install linux-image-generic
5. At this point I saw some errors like: "Invalid line in /etc/crypttab for luks-XXX -" where XXX will be the encrypted partition's UUID.
6. Edit /etc/crypttab so that it looks like: "luks-XXX /dev/sdXY none luks" /dev/sdXY should be your encrypted root partition. Alternatively you can use /dev/disk/by-uuid/XXX if you know that.
7. # update-initramfs -u
8. The previous command should without errors. Exit chroot and reboot.

Hope that helps someone.

---

