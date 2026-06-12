---
title: "Server and ZFS"
date: 2022-08-01
forum: Installation &amp; Upgrades
---

### Post by bon_the_one on 2022-08-01
Hey folks,

Can anyone advise please? I'm probs being a fool, which is why I'm stuck. Please feel free to tell me so!

I've got a UEFI Boot partition on nvme0n1p1 (10GB), then a boot ZFS mirrored across nvme0n1p2 and (by disk ID in reality) /dev/sda1 (10GB). There is a 16GB swap partition on nvme0n1p3, and root is 128GB on nvme0n1p4, with a mirror on /dev/sda2, with a spare hotswap on /dev/sdb1. All disks are identified to ZFS by ID, from /dev/disk/by-id, picking out partition numbers etc. I get all that.

I just cannot get 22.04 server to install to those ZFS pools though! This is a machine connected to my ONT, working as a firewall & router and a few other things, so I want the OS to be 24/7 and ZFS gives that reliability. Am I going to have to go back to Deb raw, or (gasp) OpenBSD (which is looking tempting at the mo...).

I'd like to use Ubuntu server tho for Canonical backup, and the ease of use deploying virtual machines on KVM. OpenBSD is a bit more of a bugger for that!

Any ideas? Should I install to an EXT4 then migrate the lot to ZFS? I tried a build based on Josphat Mutai's how to and it bombed badly. I've previously migrated root to F2FS on my NVM disks using the excellent guide by howtos.davidsebek.com but he has not hit ZFS yet!!

Any ideas really appreciated,
Thanks,

Ian

---

### Post by grahammechanical on 2022-08-01
I do not understand what you are doing but I would like to make two points.

1) The EFI boot partition (EFI System) should be FAT32. That may be the case with nvme0n1p1 but is it the case with the mirrored boot partition? Is it not ZFS?

2) My EFI System Partition (boot partition) is 537 MB. With 530MB free. Your boot partitions are 10GB. Why? Are you thinking Root partitions?

Regards

---

