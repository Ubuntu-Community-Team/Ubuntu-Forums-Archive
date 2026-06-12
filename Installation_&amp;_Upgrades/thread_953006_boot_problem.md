---
title: "boot problem"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by sminded on 2008-10-19
I'm trying to install Ubuntu Server 8.04 with a raid1 as boot and lvm managed encrypted raid10 for other partitions.

I'm now having problem booting into the new system and looking for pointers.

My system is a 4x SATAII, VIA EPIA

Heres a brief summary of what I did:
1) Install from the alternative cd
2) Configure a RAID1 with 4 partitions mounted on /boot
3) Setup root on the 4th disk /dev/sdd2
4) Finish install
5) Setup RAID10 + encryption + lvm on the first 3 disks, planning to add the 4th later
6) Migrate the system to the new logical volumes with rsync
7) Fixing crypttab/fstab/grub
8) reboot

Problem is if I select to boot from the new lvm root called /dev/mapper/vg-root, grub will just hang.
If I select the 4th disk temporary install encryption and lvm works. The root on that install is plain ext3.

How do I troubleshoot? After a while I get into BusyBox. Anything I can do from there to check what the problem is?

ps. I tried using this setup directly from the install, but it did not seem to work. ds

---

