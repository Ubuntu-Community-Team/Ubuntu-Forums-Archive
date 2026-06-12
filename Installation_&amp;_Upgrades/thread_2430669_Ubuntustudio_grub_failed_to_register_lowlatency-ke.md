---
title: "Ubuntustudio: grub failed to register lowlatency-kernels during upgrade 19:04-19:10"
date: 2019-11-05
forum: Installation &amp; Upgrades
---

### Post by heldal2 on 2019-11-05
Just performed an upgrade that failed. The only boot-option available on reboot was to go to firmware (uefi) setup. Grub had not registered any of the installed Linux kernels. This is a heads-up for anyone else experiencing similar problems. It seems like the update-process fail to recognise lowlatency-kernels. 

Upon booting from an iso, mounting filesystems and setting up a chroot-environment for recovery I discovered that the script (/etc/grub.d/09_lowlatency) used to discover lowlatency-kernels by various grub-tools was missing from my install. It had been there previously because none of the previous kernel-updates had failed. The simple solution to the problem was to reinstall the package "ubuntustudio-lowlatency-settings".

---

