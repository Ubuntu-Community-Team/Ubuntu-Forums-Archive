---
title: "Installing RAID - So Close"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by Hazr0x on 2006-09-15
Hello,

I've had several attempts at installing RAID using the text installer. First I set all partitions as RAID and cofigured software RAID. But, I came much closer to installing the system when I put /boot as a regular partitions (/dev/sda1) and set and configured the rest as RAID.

However, when the system reboots, GRUB hangs at "GRUB loading, please wait...". I was wondering, is this because of the bootable flag? I've been setting it on /boot, but I was wondering if it should be set somewhere else.

Thanks!

Haz

---

