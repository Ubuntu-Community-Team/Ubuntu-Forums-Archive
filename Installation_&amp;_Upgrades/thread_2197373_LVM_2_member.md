---
title: "LVM_2 member"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by nibal on 2014-01-03
Hi,

Doing a new installation of Ubuntu 12.04 LTS 64x. I do the partitioning myself, and asign a seperate partition for /boot with ext2 fs. When I try to reboot, grub stalls with error "Bad arch elf magic". Trying to rescue and install grub-uefi package, I cannot mount /boot because of unknown filesystem "LVM_2 memeber". How can i disable LVM during partitioning when installing?

TIA,
Nikos

---

### Post by nibal on 2014-01-03
Fixed it. From rescue environment used fdisk to delete and readd boot partition. Then formatted with ext2, mounted and reinstalled kernel and grub.

---

### Post by nibal on 2014-01-03
> **nibal said:**
> Fixed it. From rescue environment used fdisk to delete and readd boot partition. Then formatted with ext2, mounted and reinstalled kernel and grub.


Actually didn't work :(. There are a whole bunch of other files in /boot/grub, that reinstalling grub and kernel didn't help. Ended up witth an unbootable system with the warning "Very low graphics" and no mouse or keyboard.
This seems to be an installation bug of the 64x 12.04. The 32x version doesn't put /boot on LVM2! Any ideas on how to disable it during installation of 64x 12.04?

TIA,
Nikos

---

### Post by nibal on 2014-01-03
> **nibal said:**
> Actually didn't work :(. There are a whole bunch of other files in /boot/grub, that reinstalling grub and kernel didn't help. Ended up witth an unbootable system with the warning "Very low graphics" and no mouse or keyboard.
This seems to be an installation bug of the 64x 12.04. The 32x version doesn't put /boot on LVM2! Any ideas on how to disable it during installation of 64x 12.04?

TIA,
Nikos


I got rid of the LVM problem. Had to also do a grub-install /dev/sda to populate correctly my /boot/grub directory. So I am left only with the UEFI issue. But that's another thread ;-)

---

