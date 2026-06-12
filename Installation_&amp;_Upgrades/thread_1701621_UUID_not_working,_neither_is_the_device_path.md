---
title: "UUID not working, neither is the device path"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by ddivney on 2011-03-06
I finally convinced my dad to dual boot ubuntu on his netbook (a toshiba nb305). I installed everything, but when the time comes to boot, it gives the "ALERT! /dev/disk/by-uuid xxxxxxxxxxx does not exist" error. 

I triple checked the UUID for the partition in /boot/grub/grub.cfg, and compared it against /boot/fstab/ and the output of blkid. They all matched. I then tried to change the UUID to a device path when booting in grub, but after a few live boots, I realized the computer will switch the HHD from sda to sdb to sdc and back again depending on how it is feeling at the time.

Apparently, to solve this, one must use UUIDs. Catch-22 anyone?

---

