---
title: "grub2, lvm2 and /boot/grub/device.map errors"
date: 2018-06-10
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2018-06-10
Over the last several weeks I have been upgrading my servers running 16.04 LTS in preparation for moving to 18.04.1 LTS when it becomes available. I have been replacing motherboards, adding storage and generally cleaning things up.

I ran across a strange condition, which I eventually figured out but it took some luck.

All of my servers run software raid (mdadm) with lvm on top. Some of my servers were still running grub-legacy. I never saw a need to upgrade them but replacing all of the storage sort of demanded it. Most of the servers went OK but one would not boot, it dropped me into the "grub repair>" with and error message that device "lvmibh0jacD-02f0-XV2A ..." could not be located. after futzing around with it for a good while I discovered the the upgrade process had created a file /boot/grub/device.map that contained UUID entries for lvm Logical Volumes as (hd0) and (hd1), but Grub2 couldn't find them. 

The fix is pretty easy if a little complicated.
I then ran "sudo apt update' installed mdadm (i don't know why it isn't on the default iso images, it less that 2 MB). I assembled the arrays and activated the volume groups. Next I mounted root and /boot on /mnt, bound the essential virtual file systems.  In the a live session I edited the file /boot/grub/device.map to delete those entries and make sure the remaining devices are identified as (hd0), (hd1) etc. then I chroot to /mnt. In the chroot environment I then ran grub-install on my all hard drives and updated the grub configurations. Reboot and everything worked.

The chroot process is written out in detail at [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)  under the chroot method of fixing a broken system. I know most people recommend using boot repair, but I've never had much success with it.

I hope this helps someone. I may even need it again someday.

---

