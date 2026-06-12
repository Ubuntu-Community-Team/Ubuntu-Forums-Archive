---
title: "Filesystem not mounted after upgrade to 8.04"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by ubnewbie2 on 2008-04-29
I just upgraded to 8.04 from 7.10, and on reboot, it complains that /dev/hda1 has a bad superblock and it falls back to a command prompt.  The system is on /dev/sda1, so I <ctrl-D> and it completes booting successfully.

In /etc/fstab, I have /dev/hda1 (a large IDE drive with a lot of data on it) being mounted automatically, but obviously it is failing.

Running gparted, I see that it thinks I have /dev/sda1 and /dev/sdba as my drives.  I edited /etc/fstab to mount /dev/sdb1 instead of /dev/hda1, and now it works!

So what gives?  Does the new kernel name devices differently, and IDE PATA devices have similar naming to SATA drives?  If so, this is a point missed by the upgrade.

---

### Post by lemming465 on 2008-05-05
Yes, when the Linux kernel converted to new IDE drivers, all of the disks started getting named sd*.  I don't know why the upgrade got it wrong, though this is an example of why Ubuntu tends to like mounting things by UUID rather than by partition name.  Not that UUID mounts don't have their own failure modes, notably when partitions get reformatted and change UUID. Glad you got it worked out.

---

