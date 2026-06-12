---
title: "[SOLVED] Swap partition error after upgrading to 10.04"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by byline on 2010-07-05
One problem that had persisted since my upgrade to 10.04 was that the  swap partition was  not automatically mounted on boot-up, so I had to do  that manually by  typing sudo swapon -a /dev/sda1 in the  terminal. Later on, hubby added a swapon command to  /etc/rc.local, but that was actually more of a workaround than an actual solution.

Here's what hubby has figured out: the cause of this issue is that  /dev/sda1 is an old swap partition that was formatted a few years ago  and (apparently) does not contain a UUID in the superblock which Ubuntu  10.04 now requires in /etc/fstab.   No listing of a UUID link to  /dev/sda1 (ls -l /dev/disk/by-uuid) and trying to use sudo tune2fs -U  random /dev/sda1 indicated a UUID could not just be added.

So under System, Administration used Disk Utility to reformat /dev/sda1  and now (tada!) there's a symlink to /dev/sda1 in /dev/deisk/by-uuid.   Copied the symlink name into the entry for /dev/sda1 in /etc/fstab (sudo  gedit /etc/fstab) and after a cold  reboot swap was automatically used.

---

