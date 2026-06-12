---
title: "why does boot fsck hang with 2.6.23-2[2-4]?"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by iaw4 on 2010-08-24
My system has two kernels: 2.6.32-21 (came with 10.04) and 2.6.32-24 (pushed by update).  when I boot the first, everything works fine.  when I boot the second, fsck just hangs.  I can ctrl-alt-del, but it just doesn't continue.  Ctrl-C does nothing.

now, I know that the boot process stops on an fsck for a /dev/md1 device (identified via uuid).  (these kernels are the -server varieties of the kernels).  I can see just before the screen flashes by that RAID6 was loaded.  (It goes by too quickly, so I cannot see whether the RAID1 module is loaded, and/or whether /dev/md1 exists or what /dev/disk/by-uuid/* are.)

[LIST=1]
[*]How do I get the fsck.ext4 during boot to be a lot more verbose about what it thinks it is doing??
[*]How do I get a simple program (fdisk -l /dev/md1) to be executed the instant just before the fsck?  (this must be after the screen resolution switches, which happens just before the fsck.)
[*]How do I keep the boot.log from being overwritten?  the problem is that I cannot copy it, of course, when it hangs.
[/LIST]

help appreciated.

/iaw

---

