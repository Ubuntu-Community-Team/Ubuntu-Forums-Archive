---
title: "Installing Ubuntu 7.10 on LVM on top of fakeraid (raid1)"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by fbormann on 2008-02-18
Hi!

I'm trying to install ubuntu 7.10 using LVM and fakeraid (ICH7R controller) on a raid1 disk. I get both fakeraid and LVM to work by itself, but when I try to use both at the same time, I don't see my fakeraid disks in /dev/mapper (isw_blafasel<partition_no>)  anymore. It seems, the moment I create some logical volumes in LVM, the initrd of the installed system fails to run "dmraid -a yes" (I get some error messages) and LVM just mounts its partitions from one of the raid1 disks, corrupting the raid1. From the live CD (desktop install) however, the same setup works fine, when I install dmraid first and LVM second. Seems to be a problem with the initrd (perhaps not bringing up dmraid and lvm in the correct order?). Anyone have some suggestions or a solution for this problem?

---

