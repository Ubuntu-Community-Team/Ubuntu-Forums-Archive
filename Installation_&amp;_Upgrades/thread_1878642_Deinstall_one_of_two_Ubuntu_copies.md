---
title: "Deinstall one of two Ubuntu copies"
date: 2011-11-10
forum: Installation &amp; Upgrades
---

### Post by piphonom on 2011-11-10
Hello!

I have two Ubuntu copies located at one hard drive. The first copy is located in /dev/sda1. It is ext4 bootable partition. The second partition is Container for Logical Partitions. It is devided to 3 logical partitions. First logical partition is ext4 fs type and contain the second copy of Ubuntu. Two other partitions is swaps for Ubuntu first and second. How can I safely remove the second Ubuntu copy and allocate its disc space to the first Ubuntu copy?

Thanks!

---

### Post by darkod on 2011-11-10
If by allocating space you mean to extend /dev/sda1 to include this space, it's not simple. First you would need to delete the partition containing the second copy of ubuntu. Once that is unallocated space, you would need to shrink the extended partition /dev/sda2 so that it doesn't include the unallocated space.
Once the unallocated space is "outside" of the extended partition, you have to extend /dev/sda1 to include it.

Another much easier option is to simply format the partition with the second ubuntu, run sudo update-grub so that grub will delete this second copy from the boot menu, and then simply use the newly formatted partition as separate mount point, for example /data. It will be easily accessible from your main ubuntu.

---

### Post by piphonom on 2011-11-10
darkod, thank you for your answer! I will try to use second way.

---

### Post by oldfred on 2011-11-10
I agree with Darko on a separate data partition. For new users and a new install I usually suggest a separate /home which you could still do. If more familiar with Linux many of us use separate data partition(s).

Which Linux controls booting? The MBR has grub from one or the other install and you need to be sure your grub in the MBR is the one you want to keep. If the one you want is first in the menu when you boot you are ok, if not you need to also reinstall grub to the MBR after booting into the one you want.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
[COLOR=Red]sudo grub-install /dev/sda[/COLOR]

sudo update-grub

---

