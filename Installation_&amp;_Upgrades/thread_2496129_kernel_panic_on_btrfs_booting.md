---
title: "kernel panic on btrfs booting"
date: 2024-03-14
forum: Installation &amp; Upgrades
---

### Post by jduns on 2024-03-14
Today I have installed Kubuntu (without modifying EFI, with ```
ubiquity -b 
``` option). 
I choose **btrfs** as filesystem, and the root is with subvolumes (@ and @home).
I had to add **symlinks** to the root folder so that update-grub, in KDE-Neon (on the same PC) could recognize Kubuntu.
The new Kubuntu partition is displayed without errors in KLDE-Neon.

But if I try to boot Kubuntu, I get a kernel panic error message: ```
mounting /dev on /root/run failed: no such file or directory
``` and similar others.

What should I do?
Thank you!

---

