---
title: "Unable to install GRUB in /dev/md124p1"
date: 2014-11-12
forum: Installation &amp; Upgrades
---

### Post by joe-murray on 2014-11-12
I'm trying install 14.04 on a full disk RAID 10. I think the problem might be related to [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1327133](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1327133) where the problem is that the RAID is not loaded at time the boot drive is needed. FWIW, I am using the Intel Matrix Storage Manager in ROM to set up the RAID. This is recognized in Detect Disks stage as One or more drives containing MDADM containters (Intel/DDF Raid) have been found. Do you wish to activate these RAID devices? To which I answer yes.

Is there a work-around?

---

### Post by joe-murray on 2014-11-12
Let me ask this another way. At the Install the GRUB boot loader on a hard disk, how can I see what options are available for drives? The default that comes up now is /dev/md, but I would like a way to examine what is there on the system since that and /dev/sda fail.

---

### Post by joe-murray on 2014-11-12
> **joe-murray said:**
> Let me ask this another way. At the Install the GRUB boot loader on a hard disk, how can I see what options are available for drives? The default that comes up now is /dev/md, but I would like a way to examine what is there on the system since that and /dev/sda fail.

Going to the next step, something like proceed with installation without installing the GRUB boot loader, provided some text about how to boot that indicated I would need to use /dev/md125p1. When I put that in at the previous step it allowed it to proceed. #125 is the number associated with RAID configured earlier in the installation process. I assume that p1 is partition 1 on that RAID. Would be much more usable if this was the default. FWIW, I had another RAID also configured which shows up as #124, and previous installations of Ubuntu 12.04 had other devices I seem to recall. Grrr.

---

### Post by oldfred on 2014-11-13
I do not know RAID, there are many types.

But you need to install grub to either a separate /boot partition and the the MBR or the the root of the RAID.
In either case you mount the partition and install to the underlying drive/MBR/root of md.

To see details:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

One type of RAID:

 "fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

If MBR:

 sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

---

