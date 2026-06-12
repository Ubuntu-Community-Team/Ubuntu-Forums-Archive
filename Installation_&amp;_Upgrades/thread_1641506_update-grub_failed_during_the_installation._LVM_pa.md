---
title: "update-grub failed during the installation. LVM partitions"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by vangop on 2010-12-09
Hi! 
Installing 10.10 x64 from alternative cd.
I've partitioned the system to have primary /boot partition. the rest is on LVM.
The installation goes on ok, until grub. It detects win7 partitions, which is great, and asks if it's ok to install into mbr. I answer yes and get
executing update-grub failed error.
Tried to fix this from sysrescue cd (grub-install --root-dir thing), but something is wrong, I get grub shell at boot..

Can someone explain me what's wrong? Is it related so lvm (I have / on LVM, but /boot is on separate partition)
I'm new to LVM, 1st try... need some expert advice.

---

### Post by vangop on 2010-12-09
Must be related to dm-crypt.
When I create a VG and a LV for /, then extending the VG with dm-encrypted PD and creating a bunch of LV on that encrypted one - grub install fails.
When I create the / LV on the encrypted - it works..
Don't get it. Can any expert on LVM and dm-crypt comment?

---

### Post by vangop on 2010-12-12
Hi! Anyone can explain how lvm+dm-crypt+grub works?

---

