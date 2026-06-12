---
title: "mkinitramfs failure on upgrade"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by durwoodg on 2010-09-01
I know WHY this happened, but I need to know what problems it's going to cause and how I can re-install / fix the problem.

I have my /tmp folder mounted as -noexec ... so when i did a recent update to my 10.04.1 LTS server installation, I got the following errors:

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-24-server
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_H30dak/scripts/init-premount/lvm2: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_H30dak/scripts/init-top/all_generic_ide: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_H30dak/scripts/init-top/blacklist: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_H30dak/scripts/init-top/udev: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_H30dak/scripts/panic/console_setup: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_H30dak/scripts/init-bottom/udev: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_H30dak/scripts/local-premount/fixrtc: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_H30dak/scripts/local-premount/ntfs_3g: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_H30dak/scripts/local-premount/resume: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_H30dak/scripts/nfs-top/udev: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_H30dak/scripts/local-bottom/ntfs_3g: Permission denied
Press return to continue.

What should I do now? (besides, obviously, removing the -noexec flag from /tmp so this doesn't happen again!)

Thanks!

---

### Post by arrange on 2010-09-01
If (after remounting the */tmp*) you do ```
sudo dpkg --configure -a
```does the package install successfully?

---

