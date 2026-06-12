---
title: "migrate 9.04 Xen Dom0 to 11.10"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by winnall on 2011-12-27
I have a Xen 3.3 installation with 4 domU's. The dom0 and domU's all been running under Ubuntu server 9.04, but I could not never work out how to upgrade because Xen wasn't supported by Ubuntu. Now that Xen is supported again under 11.10, I have started the migration. All the domU's are now running Ubuntu server 11.10 under the old dom0.

I would now like to migrate the dom0 to 11.10 (and Xen 4) too. The problem is that the disks for the domU's are implemented using MD (RAID1) and LVM on top of a small set of disks. The dom0 has its own separate system disk.

The easiest way to get from 9.04 to 11.10 seems to be a clean install of 11.10 rather than upgrading 9.04 -> 9.10 -> 10.04 ... -> 11.10.

If I do such a clean install, can I be sure that I will be able to reconstruct the disks for the domU's with the new versions of MD and LVM? Obviously, I have to make sure that the 11.10 installation only writes to the dom0's system disk, and the MD/LVM disk set should still have the same state after the installation of the new dom0.

Any thoughts or words of warning? Or encouragement?

Steve

---

### Post by winnall on 2012-01-01
I don't know what I was worrying about...

I installed 11.10 over the existing 9.04 and the installation procedure found all my mdadm and lvm2 stuff all on its own and set them up for me.

:KS :KS :KS

Steve

---

