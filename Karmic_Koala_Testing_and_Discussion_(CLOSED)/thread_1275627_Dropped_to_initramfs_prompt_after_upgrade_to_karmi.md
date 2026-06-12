---
title: "Dropped to initramfs prompt after upgrade to karmic"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gbadger on 2009-09-26
Just posting this in case someone else has the same problem.

I upgraded from Jaunty to alpha 6 and the first reboot left me at the busybox/initramfs prompt with an "invalid operation" error which prevented the root partition from mounting.

I burned a live cd and tried to mount the disk but could not. The device was always "busy". I eventually found that device mapper was the issue and had to remove the device with the dmsetup command before mounting the drive.

I wound up using chroot to just uninstall dmsetup/dmraid etc and then it booted right up. I can't say for sure that was the right way to fix it but it got me going.

---

